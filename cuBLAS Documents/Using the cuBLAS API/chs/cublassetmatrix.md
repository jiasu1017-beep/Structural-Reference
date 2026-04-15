### 2.4.14. cublasSetMatrix()

```c++
cublasStatus_t
cublasSetMatrix(int rows, int cols, int elemSize,
                const void *A, int lda, void *B, int ldb)
```

此函数支持64位整数接口。

此函数将主机内存空间中矩阵 `A` 的 `rows x cols` 个元素的数据块复制到GPU内存空间中的矩阵 `B`。该函数假定每个元素需要 `elemSize` 字节的存储空间，并且两个矩阵均以列优先格式存储。源矩阵 `A` 和目标矩阵 `B` 的主维分别由 `lda` 和 `ldb` 给出。主维表示已分配矩阵的行数，即使仅使用其中的子矩阵。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 rows 或 cols 为负，或者 elemSize、lda、ldb 不为正数 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问GPU内存时出错 |