### 3.4.51. cublasLtEmulationDescSetAttribute()

```c++

cublasStatus_t cublasLtEmulationDescSetAttribute(
      cublasLtEmulationDesc_t emulationDesc,
      cublasLtEmulationDescAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```

此函数用于设置先前创建的仿真描述符的指定属性值。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| emulationDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体保存由此函数查询的仿真描述符。参见 cublasLtEmulationDesc_t。 |
| attr |  | 输入 | 将由此函数设置的属性。参见 cublasLtEmulationDescAttributes_t。 |
| buf |  | 输入 | 应设置为指定属性的值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 buf 为 NULL 或 sizeInBytes 与所选属性的内部存储大小不匹配。 |
| CUBLAS_STATUS_SUCCESS | 如果属性设置成功。 |

有关有效的返回码完整列表，请参见 cublasStatus_t。