### 3.4.11. cublasLtLoggerSetCallback()

```c++

cublasStatus_t cublasLtLoggerSetCallback(cublasLtLoggerCallback_t callback);


```

实验性：此函数设置日志回调函数。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| callback |  | 输入 | 指向回调函数的指针。请参阅 cublasLtLoggerCallback_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果回调函数设置成功。 |

请参阅 cublasStatus_t 获取有效返回码的完整列表。