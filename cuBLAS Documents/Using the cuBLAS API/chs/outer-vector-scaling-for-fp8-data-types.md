#### 3.1.4.3. FP8数据类型的外部向量缩放

这种缩放模式（也称为逐通道或逐行缩放）是张量级缩放的改进。与使用单个标量乘以矩阵不同，缩放因子与$A$的每一行和$B$的每一列相关联：

```

\[D_{ij} = \alpha \cdot scale_A^i \cdot scale_B^j \sum_{l=1}^k a_{il}\cdot b_{lj} + \beta \cdot scale_C \cdot C_{ij}.\]
```

值得注意的是，$scale_D$不受支持，因为$D$唯一支持的精度是`CUDA_R_16F`、`CUDA_R_16BF`和`CUDA_R_32F`。

要启用外部向量缩放，必须将`CUBLASLT_MATMUL_DESC_A_SCALE_MODE`和`CUBLASLT_MATMUL_DESC_B_SCALE_MODE`属性设置为`CUBLASLT_MATMUL_MATRIX_SCALE_OUTER_VEC_32F`，同时不得修改其他所有缩放模式。

使用此缩放模式时，$scale_A$和$scale_B$必须分别是长度为$M$和$N$的向量。