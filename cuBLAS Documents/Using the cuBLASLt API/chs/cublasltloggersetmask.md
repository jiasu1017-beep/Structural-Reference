### 3.4.15. cublasLtLoggerSetMask()

```c++

cublasStatus_t cublasLtLoggerSetMask(int mask);

```

试验性：此函数设置日志掩码的值。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| mask |  | 输入 | 日志掩码的值。请参阅 cuBLASLt 日志记录。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果日志掩码已成功设置。 |

有关有效的返回代码的完整列表，请参阅 cublasStatus_t。