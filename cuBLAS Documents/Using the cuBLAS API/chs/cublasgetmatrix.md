### 2.4.15. cublasGetMatrix()

```c++
cublasStatus_t
cublasGetMatrix(int rows, int cols, int elemSize,
                const void *A, int lda, void *B, int ldb)
```

此函数支持64位整数接口。

此函数将`rows x cols`个元素组成的块从GPU内存空间中的矩阵`A`复制到主机内存空间中的矩阵`B`。假设每个元素需要`elemSize`字节的存储空间，且两个矩阵均以列主序格式存储，源矩阵`A`和目标矩阵`B`的前导维度分别由`lda`和`ldb`给出。前导维度表示已分配矩阵的行数，即使只使用其子矩阵也是如此。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数rows或cols为负，或elemSize、lda、ldb不为正数。 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问GPU内存时出错 |