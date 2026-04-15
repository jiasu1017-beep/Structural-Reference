### 3.4.28. cublasLtMatmulDescGetAttribute()

```c++
cublasStatus_t cublasLtMatmulDescGetAttribute(
      cublasLtMatmulDesc_t matmulDesc,
      cublasLtMatmulDescAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);
```

此函数返回之前创建的矩阵乘法描述符的查询属性值。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| matmulDesc |  | 输入 | 指向之前创建的结构体的指针，该结构体包含此函数查询的矩阵乘法描述符。请参阅 cublasLtMatmulDesc_t。 |
| attr |  | 输入 | 此函数将检索的属性。请参阅 cublasLtMatmulDescAttributes_t。 |
| buf |  | 输出 | 包含此函数检索到的属性值的内存地址。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |
| sizeWritten |  | 输出 | 仅在返回值为 CUBLAS_STATUS_SUCCESS 时有效。如果 sizeInBytes 非零：则 sizeWritten 是实际写入的字节数；如果 sizeInBytes 为零：则 sizeWritten 是写入完整内容所需的字节数。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 sizeInBytes 为 0 且 sizeWritten 为 NULL，或 sizeInBytes 非零但 buf 为 NULL，或 sizeInBytes 与所选属性的内部存储大小不匹配 |
| CUBLAS_STATUS_SUCCESS | 如果属性值已成功写入用户内存。 |

有关有效返回代码的完整列表，请参阅 cublasStatus_t。