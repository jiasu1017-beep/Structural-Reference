## 3.1.4.5.1. 缩放因子布局

> **注意**

注意
缩放因子的起始地址必须按16字节对齐。

> **注意**

注意
M 和 N 必须为4的倍数。

然后，对于 `CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F` 缩放模式，缩放因子为：

- 对于 A，M-major，形状为 M × L（M-major 表示沿 M 维度的元素在内存中是连续的）
- 对于 B，N-major，形状为 N × L。

对于 `CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F` 缩放模式，缩放因子为 K-major，且连续列之间的步长必须为4的倍数。设 $L_4 = \lceil L \rceil_4$，其中 $\lceil \cdot \rceil_4$ 表示向上取整至4的倍数。然后

- 对于 A，缩放因子的形状为 $L_4 \times \lceil \frac{M}{128} \rceil$，
- 对于 B，缩放因子的形状为 $L_4 \times \lceil \frac{N}{128} \rceil$。