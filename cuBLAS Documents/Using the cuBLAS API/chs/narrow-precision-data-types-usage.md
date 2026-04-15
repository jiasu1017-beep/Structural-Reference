### 3.1.4. 窄精度数据类型用法

这里所说的*窄精度数据类型*最初作为8位浮点数据类型（FP8）在Ada和Hopper GPU（计算能力8.9及以上）中引入，旨在进一步加速矩阵乘法运算。有两种可用的FP8类型：

- `CUDA_R_8F_E4M3`设计为在比半精度更小的动态范围内保持精确。E4和M3分别表示4位指数和3位尾数。更多详细信息，请参见`__nv_fp8_e4m3`。
- `CUDA_R_8F_E5M2`设计为在类似于半精度的动态范围内保持精确。E5和M2分别表示5位指数和2位尾数。更多信息请参见`__nv_fp8_e5m2`。

> **Note**

注意
除非另有说明，FP8指的是`CUDA_R_8F_E4M3`和`CUDA_R_8F_E5M2`两种类型。

在Blackwell GPU（计算能力10.0及以上）中，cuBLAS增加了对4位浮点数据类型（FP4）`CUDA_R_4F_E2M1`的支持。E2和M1分别表示2位指数和1位尾数。更多详细信息，请参见[`__nv_fp4_e2m1`](https://docs.nvidia.com/cuda/cuda-math-api/cuda_math_api/struct____nv__fp4__e2m1.html)。

为了保持精度，窄精度的数据需要在计算前进行缩放或反量化，并在计算后进行量化。cuBLAS提供了几种缩放因子的应用模式，定义在`cublasLtMatmulMatrixScale_t`中，并通过`CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE`属性进行配置（其中`X`代表`A`、`B`、`C`、`D`、`D_OUT`或`EPILOGUE_AUX`；参见`cublasLtMatmulDescAttributes_t`）。缩放模式概述见下表，更多详细信息在后续章节中介绍。

| 模式 | 支持的计算能力 | 张量值数据类型 | 缩放因子数据类型 | 缩放因子布局 |
| --- | --- | --- | --- | --- |
| 张量级缩放 | 8.9+ | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_32F 1 | 标量 |
| 外向量缩放 | 9.0 | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_32F | 向量 |
| 128元素1D块缩放 | 9.0 | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_32F | 张量 |
| 128x128元素2D块缩放 | 9.0 | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_32F | 张量 |
| 32元素1D块缩放 | 10.0+ | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_8F_UE8M0 2 | 分块张量 4 |
| 16元素1D块缩放 | 10.0+ | CUDA_R_4F_E2M1 | CUDA_R_8F_UE4M3 3 | 分块张量 4 |
| 实验性：按批次张量级缩放 | 10.0+ | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_32F 1 | 指针数组 |

**注意：**

**1(1,2)**
: 数据类型为`CUDA_R_32F`的缩放因子可以为负数，并且按原样应用，不会先取绝对值。

**2**
: `CUDA_R_8F_UE8M0`是一种8位无符号纯指数浮点数据类型。更多信息请参见`__nv_fp8_e8m0`。

**3**
: `CUDA_R_8F_UE4M3`是`CUDA_R_E4M3`的无符号版本。符号位被忽略，因此提供此枚举值以方便使用。

**4(1,2)**
: 有关更多详细信息，请参见1D块缩放因子布局。

> **Note**

注意
缩放仅适用于窄精度矩阵乘法。如果为非窄精度矩阵乘法设置了任何缩放因子，cuBLAS将返回错误。此外，缩放通常仅支持窄精度张量。如果为非窄精度张量设置了相应的缩放因子，cuBLAS将返回错误。唯一的例外是，C张量允许使用张量级缩放模式的非窄数据类型缩放。

> **Note**

注意
仅当任何矩阵的`cublasLtBatchMode_t`设置为`CUBLASLT_BATCH_MODE_POINTER_ARRAY`时，才支持张量级缩放。

#### 3.1.4.1. FP8数据类型的张量级缩放

当所有FP8精度张量的`CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE`属性（其中`X`代表`A`、`B`、`C`、`D`或`EPILOGUE_AUX`；参见`cublasLtMatmulDescAttributes_t`）设置为`CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F`（这是FP8张量的默认值）时，启用张量级缩放。在这种情况下，cuBLAS中的矩阵乘法运算定义如下（为便于说明，假设所有张量都使用FP8精度）：

```

\[D = scale_D \cdot (\alpha \cdot scale_A \cdot scale_B \cdot \text{op}(A) \text{op}(B) + \beta \cdot scale_C \cdot C).\]
```

这里$A$、$B$和$C$是输入张量，而$scale_A$、$scale_B$、$scale_C$、$scale_D$、$\alpha$和$\beta$是输入标量。这与其它矩阵乘法例程不同，因为为每个矩阵添加了缩放因子。$scale_A$、$scale_B$和$scale_C$用于反量化，$scale_D$用于量化。请注意，所有缩放因子都是乘性应用的。这意味着有时需要根据应用上下文使用缩放因子或其倒数。有关FP8的更多信息，请参见`cublasLtMatmul()`和`cublasLtMatmulDescAttributes_t`。

对于此类矩阵乘法，尾函数和中间值的绝对最大值计算如下：

```

\[\begin{split}Aux_{temp} & = \alpha \cdot scale_A \cdot scale_B \cdot \text{op}(A) \text{op}(B) + \beta \cdot scale_C \cdot C + bias, \\
D_{temp} & = \mathop{Epilogue}(Aux_{temp}), \\
amax_{D} & = \mathop{absmax}(D_{temp}), \\
amax_{Aux} & = \mathop{absmax}(Aux_{temp}), \\
D & = scale_D * D_{temp}, \\
Aux & = scale_{Aux} * Aux_{temp}. \\\end{split}\]
```

这里$Aux$是矩阵乘法的辅助输出，由传递给尾函数（如GELU）的值组成，$scale_{Aux}$是可选的缩放因子，可应用于$Aux$，而$amax_{Aux}$是缩放前$Aux$中的最大绝对值。更多信息，请参见`cublasLtMatmulDescAttributes_t`中的`CUBLASLT_MATMUL_DESC_AMAX_D_POINTER`和`CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_AMAX_POINTER`属性。

> **Note**

注意
如上方程式所示，偏置在计算$Aux_{temp}$之前应用。

#### 3.1.4.2. 实验性：FP8数据类型的按批次张量级缩放

当所有FP8精度张量的`CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE`属性（其中`X`代表`A`、`B`、`C`、`D`或`EPILOGUE_AUX`；参见`cublasLtMatmulDescAttributes_t`）设置为`CUBLASLT_MATMUL_MATRIX_SCALE_PER_BATCH_SCALAR_32F`时，启用按批次张量级缩放。

按批次张量级缩放是张量级缩放的一种变体，只是批次中的每个矩阵都有其自己的缩放因子。

使用按批次张量级缩放时，$scale_A$、$scale_B$、$scale_C$、$scale_D$和$scale_{Aux}$必须是长度为`CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT`的设备指针数组。

> **Note**

注意
仅当所有矩阵的`cublasLtBatchMode_t`设置为`CUBLASLT_BATCH_MODE_GROUPED`时，才支持按批次张量级缩放。

#### 3.1.4.3. FP8数据类型的外向量缩放

此缩放模式（也称为逐通道或逐行缩放）是张量级缩放的改进。不是用单个标量乘以矩阵，而是为$A$的每一行和$B$的每一列关联一个缩放因子：

```

\[D_{ij} = \alpha \cdot scale_A^i \cdot scale_B^j \sum_{l=1}^k a_{il}\cdot b_{lj} + \beta \cdot scale_C \cdot C_{ij}.\]
```

值得注意的是，不支持$scale_D$，因为$D$唯一支持的精度是`CUDA_R_16F`、`CUDA_R_16BF`和`CUDA_R_32F`。

要启用外向量缩放，必须将`CUBLASLT_MATMUL_DESC_A_SCALE_MODE`和`CUBLASLT_MATMUL_DESC_B_SCALE_MODE`属性设置为`CUBLASLT_MATMUL_MATRIX_SCALE_OUTER_VEC_32F`，而所有其他缩放模式不得修改。

使用此缩放模式时，$scale_A$和$scale_B$必须是长度分别为$M$和$N$的向量。

#### 3.1.4.4. FP8和FP4数据类型的16/32元素1D块缩放

1D块缩放旨在克服使用单个标量缩放整个张量的局限性。在[OCP MXFP](https://www.opencompute.org/documents/ocp-microscaling-formats-mx-v1-0-spec-final-pdf)规范中有更详细的描述，因此这里仅作简要概述。块缩放意味着同一16或32元素块内的相邻值元素共享一个缩放因子。

目前，支持FP8精度和FP4精度张量的块缩放，不支持混合精度。要启用块缩放，必须将`CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE`属性（其中`X`代表`A`、`B`、`C`、`DOUT`或`EPILOGUE_AUX`；参见`cublasLtMatmulDescAttributes_t`）设置为`CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0`（适用于所有FP8精度张量）或`CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3`（适用于所有FP4精度张量）。

使用块缩放时，cuBLAS中的矩阵乘法运算定义如下（为便于说明，假设所有张量都使用窄精度）。我们大致遵循OCP MXFP规范的表示法。

首先，缩放块（或OCP MXFP规范中的MX兼容格式向量）是一个元组$x = \left(S^x, \left[x^i\right]_{i=1}^k\right)$，其中$S^x$是共享缩放因子，每个$x^i$使用FP8或FP4数据类型存储。

两个缩放块$x = \left(S^x, \left[x^i\right]_{i=1}^{k}\right)$和$y = \left(S^y, \left[y^i\right]_{i=1}^{k}\right)$的点积定义如下：

```

\[Dot(x, y) = S^x S^y \cdot \sum_{i=1}^{k} x^i y^i.\]
```

对于$n$个块序列$X = \{x_j\}_{j=1}^n$和$Y = \{y_j\}_{j=1}^n$，广义点积定义为：

```

\[DotGeneral(X, Y) = \sum_{j=1}^n Dot(x_j, y_j).\]
```

广义点积可用于通过将$A$和$B$在$K$维度上每$k$个元素组合一个缩放因子来定义矩阵乘法（为简单起见，假设$K$可被$k$整除无余数）：

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

$Quantize$在1D块量化部分有解释，$Dequantize$定义为：

```

\[Dequantize\left(\left\{scale_C, C\right\})\right)_{i,j} = {scale_C}_{i/k,j} \cdot C_{i,j}.\]
```

> **Note**

注意
除了在量化期间计算的\(scale_D^{out}\)之外，对于$D$还有一个输入标量张量级缩放因子\(scale_D^{in}\)，仅当缩放因子使用`CUDA_R_8F_UE4M3`数据类型时才可用。它用于在量化之前"压缩"计算的值。

##### 3.1.4.4.1. 1D块量化

考虑$M$维度中$D$的$k$个元素的单个块：$D^b_{fp32} = \left[d^i_{fp32}\right]_{i=1}^k$。部分块的量化按缺失值为零处理。设$Amax(DType)$为目标精度中可表示的最大值。

以下计算步骤适用于输出和缩放因子数据类型的所有组合。

1. 计算块绝对最大值\(Amax(D^b_{fp32}) = max(\{|d_i|\}_{i=1}^k)\)。
2. 以单精度计算块缩放因子为\(S^b_{fp32} = \frac{Amax(D^b_{fp32})}{Amax(DType)}\)。

**计算带UE8M0缩放的FP8缩放和转换因子**

> **Note**

注意
除非另有说明，假定使用RNE舍入。

计算包括以下步骤：

1. 从$S^b_{fp32}$中提取块缩放因子的指数（无偏置调整）作为整数$E^b_{int}$和尾数作为定点数$M^b_{fixp}$（实际实现直接操作位表示）。
2. 向上舍入块指数，保持其在UE8M0可表示值范围内：\(E^b_{int} = \left\{\begin{array}{ll} E^b_{int} + 1, & \text{if } S^b_{fp32} \text{ is a normal number and }  E^b_{int} < 254 \text{ and } M^b_{fixp} > 0 \\ E^b_{int} + 1, & \text{if } S^b_{fp32} \text{is a denormal number and } M^b_{fixp} > 0.5, \\ E^b_{int}, & \text{otherwise.} \end{array}\right.\)
3. 计算块缩放因子为\(S^b_{ue8m0} = 2^{E^b_{int}}\)。请注意，UE8M0数据类型的指数偏置为127。
4. 计算块转换因子为\(R^b_{fp32} = \frac{1}{fp32(S^b_{ue8m0})}\)。

> **Note**

注意
上述算法与OCP MXFP建议的舍入方案不同。

**计算带UE4M3缩放的FP4缩放和转换因子**

这里我们假设算法提供了一个预计算的张量级输入缩放因子$scale_D^{in}$，在一般情况下计算如下：

```

\[scale_D^{in} = \frac{Amax(e2m1) \cdot Amax(e4m3)}{Amax(D_{temp})},\]
```

其中$Amax(D_{temp})$是量化前矩阵乘法结果的全局绝对最大值。由于计算此值需要知道整个计算的结果，实际上使用的是来自例如前一次迭代的近似值。

计算包括以下步骤：

1. 计算块缩放因子的窄精度值\(S^b_{e4m3} = e4m3(S^b_{fp32})\)。
2. 计算块转换因子为\(R^b_{fp32} = \frac{1}{fp32(S^b_{e4m3})}\)。

**应用转换因子**

对于每个$i = 1 \ldots k$，计算$d^i = DType(d^i_{fp32} \cdot R^b_{fp32})$。结果量化块为$\left(S^b, \left[d^i\right]_{i=1}^k\right)$，其中对于带UE8M0缩放因子的FP8，$S^b$为$S^b_{ue8m0}$，对于带UE4M3缩放因子的FP4，$S^b$为$S^b_{ue4m3}$。

##### 3.1.4.4.2. 1D块缩放因子布局

缩放因子使用分块布局存储。下图显示了每个128x4块在内存中的布局方式。内存中的偏移量从左到右增加，然后从上到下增加。

下图显示了每个128x4块在内存中的布局方式。内存偏移量从左到右增加，然后从上到下增加。

以下伪代码可用于将`inner`（对于A和B为K，对于C或D为M）和`outer`（对于A为M，对于B、C和D为N）索引转换为块内的线性`offset`，反之亦然：

```c++

// Indices -> offset
// 索引 -> 偏移量
offset = (outer % 32) * 16 + (outer / 32) * 4 + inner

// Offset -> Indices
// 偏移量 -> 索引
outer = ((offset % 16) / 4) * 32 + (offset / 16)
inner = (offset % 4)


```

单个缩放因子块在缩放模式为`CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3`时应用于128x64块，在缩放模式为`CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0`时应用于128x128块。

多个块按行主序排列。下图显示了一个示例。内存偏移量从左到右增加，然后从上到下增加。

通常，对于具有`sf_inner_dim`个缩放因子每行的缩放因子张量，具有左上角坐标`(sf_outer, sf_inner)`的块的偏移量（使用与上述相同的矩阵坐标对应关系）可使用以下伪代码计算：

```c++

// Indices -> offset
// 索引 -> 偏移量
// 注意：由于分块布局，sf_inner是4的倍数
offset = (sf_inner + sf_outer * sf_inner_dim) * 128


```

> **Note**

注意
缩放因子的起始地址必须16字节对齐。

> **Note**

注意
请注意，上述布局不允许转置。这意味着即使输入张量可以转置，缩放因子的布局也不会改变。

> **Note**

注意
请注意，当张量维度不是上述块大小的倍数时，仍需要分配完整块用于存储，并用零填充越界值。此外，在写入输出缩放因子时，内核可能会写入额外的零，因此最好不要对越界值的持久性做任何假设。

#### 3.1.4.5. FP8数据类型的128元素1D和128x128 2D块缩放

这两种缩放模式将16/32元素1D块缩放（用于FP8和FP4数据类型）中描述的缩放方法原理应用于Hopper GPU架构。但是，这里的缩放数据类型是`CUDA_R_32F`，且可以为$A$和$B$使用不同的缩放模式，$D$唯一支持的精度是`CUDA_R_16F`、`CUDA_R_16BF`和`CUDA_R_32F`。

要启用此缩放模式，必须将`CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE`属性（其中`X`代表`A`或`B`）设置为`CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F`或`CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F`，而所有其他缩放模式不得修改。下表显示了支持的组合：

| CUBLASLT_MATMUL_DESC_A_SCALE_MODE | CUBLASLT_MATMUL_DESC_B_SCALE_MODE | 支持？ |
| --- | --- | --- |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | 是 |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | 是 |
| CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | 是 |
| CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | 否 |

使用16/32元素1D块缩放（用于FP8和FP4数据类型）中的表示法，我们可以按以下方式定义$A$第$i$行的缩放块序列：

```

\[\begin{split}L & = \lceil \frac{K}{128} \rceil, \\
A^{128}_i & = \left\{{scale_A}_{i,b}, \left[A_{i,(b-1)128+l}\right]_{l=1}^{128}\right\}_{b=1}^L, \text{(这是128元素1D块缩放)} \\
\\
p & = \lceil \frac{i}{128} \rceil, \\
A^{128 \times 128}_i & = \left\{{scale_A}_{p,b}, \left[A_{i,(b-1)128+l}\right]_{l=1}^{128}\right\}_{b=1}^L. \text{(这是128x128元素2D块缩放)} \\\end{split}\]
```

$B$的定义类似。然后矩阵乘法如16/32元素1D块缩放（用于FP8和FP4数据类型）中所定义，显著的区别是使用2D块缩放时，单个缩放因子用于整个128x128元素块。

##### 3.1.4.5.1. 缩放因子布局

> **Note**

注意
缩放因子的起始地址必须16字节对齐。

> **Note**

注意
$M$和$N$必须是4的倍数。

对于`CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F`缩放模式，缩放因子为：

- $A$为$M$主序，形状为$M \times L$（$M$主序意味着$M$维度上的元素在内存中是连续的），
- $B$为$N$主序，形状为$N \times L$。

对于`CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F`缩放模式，缩放因子为$K$主序，且连续列之间的步长必须是4的倍数。设$L_4 = \lceil L \rceil_4$，其中$\lceil \cdot \rceil_4$表示向上舍入到4的最近倍数。然后：

- 对于$A$，缩放因子的形状为$L_4 \times \lceil \frac{M}{128} \rceil$，
- 对于$B$，缩放因子的形状为$L_4 \times \lceil \frac{N}{128} \rceil$。