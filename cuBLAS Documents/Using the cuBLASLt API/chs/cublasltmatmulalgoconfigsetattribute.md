### 3.4.21. cublasLtMatmulAlgoConfigSetAttribute()

```c++

cublasStatus_t cublasLtMatmulAlgoConfigSetAttribute(
      cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulAlgoConfigAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```

此函数用于设置已初始化的 `cublasLtMatmulAlgo_t` 描述符的指定配置属性的值。配置属性是 `cublasLtMatmulAlgoConfigAttributes_t` 类型的枚举值。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| algo |  | 输入 | 指向先前创建的不透明结构的指针，该结构保存矩阵乘法算法描述符。请参阅 `cublasLtMatmulAlgo_t`。 |
| attr |  | 输入 | 将由此函数设置其值的配置属性。请参阅 `cublasLtMatmulAlgoConfigAttributes_t`。 |
| buf |  | 输入 | 要设置给配置属性的值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 buf 为 NULL 或 sizeInBytes 与所选属性的内部存储大小不匹配。 |
| CUBLAS_STATUS_SUCCESS | 如果属性设置成功。 |

有关有效的返回代码完整列表，请参阅 `cublasStatus_t`。