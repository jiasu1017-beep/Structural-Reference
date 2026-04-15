### 3.4.13. cublasLtLoggerOpenFile()

```c++
cublasStatus_t cublasLtLoggerOpenFile(const char* logFile);
```

实验性：此函数打开并设置给定路径下的日志输出文件。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| logFile |  | 输入 | 日志输出文件的路径。 |

**返回值**：

| 返回值 | 描述 |
| --- |
| CUBLAS_STATUS_SUCCESS | 日志文件已成功打开。 |

有关有效返回码的完整列表，请参阅 cublasStatus_t。