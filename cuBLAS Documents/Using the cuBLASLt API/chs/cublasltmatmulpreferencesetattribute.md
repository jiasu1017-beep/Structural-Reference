### 3.4.34. cublasLtMatmulPreferenceSetAttribute()

```c++

cublasStatus_t cublasLtMatmulPreferenceSetAttribute(
      cublasLtMatmulPreference_t pref,
      cublasLtMatmulPreferenceAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```

此函数用于设置先前创建的矩阵乘法偏好设置描述符中指定属性的值。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| pref |  | 输入 | 指向先前创建的结构体的指针，该结构体保存由此函数查询的矩阵乘法偏好设置描述符。请参阅 cublasLtMatmulPreference_t。 |
| attr |  | 输入 | 将由此函数设置的属性。请参阅 cublasLtMatmulPreferenceAttributes_t。 |
| buf |  | 输入 | 指定属性应设置到的值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 buf 为 NULL 或 sizeInBytes 与所选属性的内部存储大小不匹配。 |
| CUBLAS_STATUS_SUCCESS | 如果属性设置成功。 |

有关有效返回码的完整列表，请参阅 cublasStatus_t。