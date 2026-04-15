3.1.4.4.1. 1D Block Quantization

考虑 $D$ 在 $M$ 维度上的一个包含 $k$ 个元素的块：$D^b_{fp32} = \left[d^i_{fp32}\right]_{i=1}^k$。部分块的量化按照缺失值为零的方式进行。设 $Amax(DType)$ 为目标精度中可表示的最大值。

以下计算步骤适用于输出和缩放因子数据类型的所有组合。

1. 计算块的绝对最大值 $Amax(D^b_{fp32}) = max(\{|d_i|\}_{i=1}^k)$。
2. 以单精度计算块缩放因子 $S^b_{fp32} = \frac{Amax(D^b_{fp32})}{Amax(DType)}$。

**计算 FP8 与 UE8M0 缩放因子的缩放和转换因子**

> **注意**

除非另有说明，否则假定采用 RNE（四舍五入到最近偶数）舍入。

计算包括以下步骤：

1. 从 $S^b_{fp32}$ 中提取块缩放因子的指数（无偏置调整）作为整数 $E^b_{int}$，尾数作为定点数 $M^b_{fixp}$（实际实现直接对位表示进行操作）。
2. 向上舍入块指数，同时保持其在 UE8M0 可表示值范围内：

$$E^b_{int} = \left\{\begin{array}{ll} E^b_{int} + 1, & \text{if } S^b_{fp32} \text{ is a normal number and }  E^b_{int} < 254 \text{ and } M^b_{fixp} > 0 \\ E^b_{int} + 1, & \text{if } S^b_{fp32} \text{is a denormal number and } M^b_{fixp} > 0.5, \\ E^b_{int}, & \text{otherwise.} \end{array}\right.$$

3. 计算块缩放因子 $S^b_{ue8m0} = 2^{E^b_{int}}$。请注意，UE8M0 数据类型的指数偏置为 127。
4. 计算块转换因子 $R^b_{fp32} = \frac{1}{fp32(S^b_{ue8m0})}$。

> **注意**

上述算法与 OCP MXFP 建议的舍入方案不同。

**计算 FP4 与 UE4M3 缩放因子的缩放和转换因子**

这里我们假设算法提供了预先计算的输入张量级缩放因子 $scale_D^{in}$，在一般情况下按下式计算：

```

\[scale_D^{in} = \frac{Amax(e2m1) \cdot Amax(e4m3)}{Amax(D_{temp})},\]
```

其中 $Amax(D_{temp})$ 是量化前矩阵乘法结果的全局绝对最大值。由于计算此值需要知道整个计算的结果，在实践中通常使用上一次迭代的近似值。

计算包括以下步骤：

1. 计算块缩放因子的窄精度值 $S^b_{e4m3} = e4m3(S^b_{fp32})$。
2. 计算块转换因子 $R^b_{fp32} = \frac{1}{fp32(S^b_{e4m3})}$。

**应用转换因子**

对于每个 $i = 1 \ldots k$，计算 $d^i = DType(d^i_{fp32} \cdot R^b_{fp32})$。结果量化块为 $\left(S^b, \left[d^i\right]_{i=1}^k\right)$，其中 $S^b$ 对于 FP8 与 UE8M0 缩放因子为 $S^b_{ue8m0}$，对于 FP4 与 UE4M3 缩放因子为 $S^b_{ue4m3}$。