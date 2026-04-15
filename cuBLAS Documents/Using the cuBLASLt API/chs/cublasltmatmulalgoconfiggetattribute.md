### 3.4.20. cublasLtMatmulAlgoConfigGetAttribute()



```c++

cublasStatus_t cublasLtMatmulAlgoConfigGetAttribute(
      const cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulAlgoConfigAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


此函数返回针对已初始化的 `cublasLtMatmulAlgo_t` 描述符所查询的配置属性的值。配置属性值从枚举类型 `cublasLtMatmulAlgoConfigAttributes_t` 中检索。


**参数**：


| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| algo |  | 输入 | 指向先前创建的不透明结构的指针，该结构保存矩阵乘法算法描述符。请参见 `cublasLtMatmulAlgo_t`。 |
| attr |  | 输入 | 此函数将检索其值的配置属性。请参见 `cublasLtMatmulAlgoConfigAttributes_t`。 |
| buf |  | 输出 | 此函数返回的属性值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |
| sizeWritten |  | 输出 | 仅在返回值为 `CUBLAS_STATUS_SUCCESS` 时有效。如果 sizeInBytes 非零：则 sizeWritten 为实际写入的字节数；如果 sizeInBytes 为零：则 sizeWritten 为写入完整内容所需的字节数。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| `CUBLAS_STATUS_INVALID_VALUE` | 如果 sizeInBytes 为零且 sizeWritten 为 NULL，或如果 sizeInBytes 非零且 buf 为 NULL，或如果 sizeInBytes 与所选属性的内部存储大小不匹配 |
| `CUBLAS_STATUS_SUCCESS` | 如果属性值已成功写入用户内存。 |


请参阅 `cublasStatus_t` 以获取有效返回代码的完整列表。