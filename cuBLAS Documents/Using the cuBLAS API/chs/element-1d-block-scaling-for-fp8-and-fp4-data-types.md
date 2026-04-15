#### 3.1.4.4. FP8 和 FP4 数据类型的 16/32 元素 1D 块缩放

1D 块缩放旨在克服使用单一标量来缩放整个张量的局限性。具体细节在 [OCP MXFP](https://www.opencompute.org/documents/ocp-microscaling-formats-mx-v1-0-spec-final-pdf) 规范中有更详细的描述，这里只做简要概述。块缩放意味着同一 16 或 32 元素块内的相邻元素被分配一个共享的缩放因子。

目前，块缩放支持 FP8 精度和 FP4 精度的张量，不支持混合精度。要启用块缩放，必须将 `CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE` 属性（其中 `X` 代表 `A`、`B`、`C`、`DOUT` 或 `EPILOGUE_AUX`；参见 cublasLtMatmulDescAttributes_t）设置为 `CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0`（适用于所有 FP8 精度张量）或 `CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3`（适用于所有 FP4 精度张量）。

使用块缩放时，cuBLAS 中的矩阵乘法运算定义如下（为便于说明，假设所有张量都使用窄精度）。我们大致遵循 OCP MXFP 规范的符号表示。

首先，一个缩放块（或者说 OCP MXFP 规范中的 MX 兼容格式向量）是一个元组 $x = \left(S^x, \left[x^i\right]_{i=1}^k\right)$，其中 $S^x$ 是共享缩放因子，每个 $x^i$ 使用 FP8 或 FP4 数据类型存储。

两个缩放块 $x = \left(S^x, \left[x^i\right]_{i=1}^{k}\right)$ 和 $y = \left(S^y, \left[y^i\right]_{i=1}^{k}\right)$ 的点积定义如下：



```

\[Dot(x, y) = S^x S^y \cdot \sum_{i=1}^{k} x^i y^i.\]
```


对于 $n$ 个块的序列 $X = \{x_j\}_{j=1}^n$ 和 $Y = \{y_j\}_{j=1}^n$，广义点积定义为：



```

\[DotGeneral(X, Y) = \sum_{j=1}^n Dot(x_j, y_j).\]
```


广义点积可用于定义矩阵乘法，方法是将 $A$ 和 $B$ 在 $K$ 维度上每 $k$ 个元素组合一个缩放因子（为简单起见，假设 $K$ 能被 $k$ 整除）：



```

\[\begin{split}L & = \frac{K}{k}, \\
A_i & = \left\{{scale_A}_{i,b}, \left[A_{i,(b-1)k+l}\right]_{l=1}^{k}\right\}_{b=1}^L, \\
B_j & = \left\{{scale_B}_{i,b}, \left[B_{(b-1)k+l,j}\right]_{l=1}^{k}\right\}_{b=1}^L, \\
(\left\{scale_A, A\right\} \times \left\{scale_B, B\right\})_{i,j} & = DotGeneral(A_i, B_j).\end{split}\]
```


现在，完整的矩阵乘法可以写成：



```

\[\left\{scale_D^{out}, D\right\} = Quantize\left(scale_D^{in}\left(\alpha \cdot \left\{scale_A, \text{op}(A)\right\} \times \left\{scale_B, \text{op}(B)\right\} + \beta \cdot Dequantize(\left\{scale_C, C\right\})\right)\right).\]
```


$Quantize$ 在 1D 块量化一节中有解释，$Dequantize$ 定义为：



```

\[Dequantize\left(\left\{scale_C, C\right\})\right)_{i,j} = {scale_C}_{i/k,j} \cdot C_{i,j}.\]
```


> **注意**

注意
除了量化期间计算的 $scale_D^{out}$ 之外，还有一个输入的标量张量级缩放因子 $scale_D^{in}$，用于 $D$。该因子仅在使用 `CUDA_R_8F_UE4M3` 数据类型的缩放因子时可用。它用于在量化之前"压缩"计算值。




3.1.4.4.1. 1D 块量化

考虑 $M$ 维度上 $k$ 个元素的单个 $D$ 块：$D^b_{fp32} = \left[d^i_{fp32}\right]_{i=1}^k$。部分块的量化按缺失值为零来处理。设 $Amax(DType)$ 为目标精度可表示的最大值。

以下计算步骤适用于输出和缩放因子数据类型的所有组合。


1. 计算块的绝对最大值 \(Amax(D^b_{fp32}) = max(\{|d_i|\}_{i=1}^k)\)。
2. 以单精度计算块缩放因子 \(S^b_{fp32} = \frac{Amax(D^b_{fp32})}{Amax(DType)}\)。


**计算 FP8 与 UE8M0 缩放因子的缩放和转换因子**


> **注意**

注意
除非另有说明，否则假定使用 RNE（四舍五入到最近偶数）舍入。


计算包括以下步骤：


1. 从 $S^b_{fp32}$ 中提取块缩放因子指数（无偏置调整）作为整数 $E^b_{int}$，尾数作为定点数 $M^b_{fixp}$（实际实现直接操作位表示）。
2. 向上舍入块指数，保持其在 UE8M0 可表示值范围内：\(E^b_{int} = \left\{\begin{array}{ll} E^b_{int} + 1, & \text{if } S^b_{fp32} \text{ is a normal number and }  E^b_{int} < 254 \text{ and } M^b_{fixp} > 0 \\ E^b_{int} + 1, & \text{if } S^b_{fp32} \text{is a denormal number and } M^b_{fixp} > 0.5, \\ E^b_{int}, & \text{otherwise.} \end{array}\right.\)
3. 计算块缩放因子 \(S^b_{ue8m0} = 2^{E^b_{int}}\)。注意 UE8M0 数据类型的指数偏置为 127。
4. 计算块转换因子 \(R^b_{fp32} = \frac{1}{fp32(S^b_{ue8m0})}\)。


> **注意**

注意
上述算法与 OCP MXFP 建议的舍入方案不同。


**计算 FP4 与 UE4M3 缩放因子的缩放和转换因子**


这里我们假设算法提供了一个预计算的张量级输入缩放因子 $scale_D^{in}$，在一般情况下按下式计算



```

\[scale_D^{in} = \frac{Amax(e2m1) \cdot Amax(e4m3)}{Amax(D_{temp})},\]
```


其中 $Amax(D_{temp})$ 是量化前矩阵乘法结果的全局绝对最大值。由于计算此值需要知道整个计算的结果，在实践中通常使用上一次迭代的近似值。


计算包括以下步骤：


1. 计算块缩放因子的窄精度值 \(S^b_{e4m3} = e4m3(S^b_{fp32})\)。
2. 计算块转换因子 \(R^b_{fp32} = \frac{1}{fp32(S^b_{e4m3})}\)。


**应用转换因子**


对于每个 $i = 1 \ldots k$，计算 $d^i = DType(d^i_{fp32} \cdot R^b_{fp32})$。得到的量化块是 $\left(S^b, \left[d^i\right]_{i=1}^k\right)$，其中对于 FP8 与 UE8M0 缩放因子，$S^b$ 为 $S^b_{ue8m0}$；对于 FP4 与 UE4M3 缩放因子，$S^b$ 为 $S^b_{ue4m3}$。





3.1.4.4.2. 1D 块缩放因子布局

缩放因子使用平铺布局存储。下图显示了每个 128x4 瓦片在内存中的布局方式。内存中的偏移量从左到右递增，然后从上到下递增。





以下伪代码可用于将 `inner`（A 和 B 的 K，C 或 D 的 M）和 `outer`（A 的 M，B、C 和 D 的 N）索引转换为瓦片内的线性 `offset`，并反向转换：



```c++

// Indices -> offset
// 索引 -> 偏移量
offset = (outer % 32) * 16 + (outer / 32) * 4 + inner

// Offset -> Indices
// 偏移量 -> 索引
outer = ((offset % 16) / 4) * 32 + (offset / 16)
inner = (offset % 4)


```


当缩放模式为 `CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3` 时，单个缩放因子瓦片应用于 128x64 块；当为 `CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0` 时应用于 128x128 块。

多个块按行优先方式排列。下一张图片显示了一个示例。内存中的偏移量从左到右递增，然后从上到下递增。





一般来说，对于每个行有 `sf_inner_dim` 个缩放因子的缩放因子张量，左上角坐标为 `(sf_outer, sf_inner)` 的块的偏移量（使用与上述相同的矩阵坐标对应关系）可使用以下伪代码计算：



```c++

// Indices -> offset
//   note that sf_inner is a multiple of 4 due to the tiling layout
// 索引 -> 偏移量
//   注意，由于平铺布局，sf_inner 是 4 的倍数
offset = (sf_inner + sf_outer * sf_inner_dim) * 128


```


> **注意**

注意
缩放因子的起始地址必须 16 字节对齐。


> **注意**

注意
请注意，上述布局不允许转置。这意味着即使输入张量可以转置，缩放因子的布局也不会改变。


> **注意**

注意
请注意，当张量维度不是上述瓦片大小的倍数时，仍需分配完整的瓦片进行存储，并将超出边界的值填充为零。此外，在写入输出缩放因子时，内核可能会写入额外的零，因此最好不要对超出边界值的持久性做任何假设。