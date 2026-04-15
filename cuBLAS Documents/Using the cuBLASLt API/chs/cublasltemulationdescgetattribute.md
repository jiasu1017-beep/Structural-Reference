### 3.4.52. cublasLtEmulationDescGetAttribute()



```c++

cublasStatus_t cublasLtEmulationDescGetAttribute(
      cublasLtEmulationDesc_t emulationDesc,
      cublasLtEmulationDescAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


此函数返回先前创建的仿真描述符所属的查询属性的值。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| emulationDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体保存了此函数查询的仿真描述符。请参见 cublasLtEmulationDesc_t。 |
| attr |  | 输入 | 此函数将检索的属性。请参见 cublasLtEmulationDescAttributes_t。 |
| buf |  | 输出 | 包含此函数检索到的属性值的内存地址。 |
| sizeInBytes |  | 输入 | 用于验证的 buf 缓冲区大小（以字节为单位）。 |
| sizeWritten |  | 输出 | 仅在返回值为 CUBLAS_STATUS_SUCCESS 时有效。
如果 sizeInBytes 非零：则 sizeWritten 为实际写入的字节数；
如果 sizeInBytes 为零：则 sizeWritten 为写入完整内容所需的字节数。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 sizeInBytes 为零且 sizeWritten 为 NULL，或

如果 sizeInBytes 非零且 buf 为 NULL，或
如果 sizeInBytes 与所选属性的内部存储大小不匹配 |
| CUBLAS_STATUS_SUCCESS | 如果属性值已成功写入用户内存。 |