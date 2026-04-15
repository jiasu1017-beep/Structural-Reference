### 3.3.4. cublasLtLoggerCallback_t

cublasLtLoggerCallback_t 是一个回调函数指针类型。可以使用 cublasLtLoggerSetCallback() 设置回调函数。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| logLevel |  | Output | 参见 cuBLASLt 日志记录。 |
| functionName |  | Output | 记录此消息的 API 名称。 |
| message |  | Output | 日志消息。 |