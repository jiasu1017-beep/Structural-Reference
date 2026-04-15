### 3.4.14. cublasLtLoggerSetLevel()

```c++
cublasStatus_t cublasLtLoggerSetLevel(int level);
```

实验性：此函数用于设置日志级别的值。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| level |  | 输入 | 日志级别的值。参见 cuBLASLt 日志记录。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果该值不是有效的日志级别。参见 cuBLASLt 日志记录。 |
| CUBLAS_STATUS_SUCCESS | 如果日志级别设置成功。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。