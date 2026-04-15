### 2.4.38. cublasLoggerConfigure()

```c++
cublasStatus_t cublasLoggerConfigure(
    int             logIsOn,
    int             logToStdOut,
    int             logToStdErr,
    const char*     logFileName)
```

此函数用于在运行时配置日志记录。除此类配置方式外，还可以通过特殊的**环境变量**来配置日志记录，这些环境变量会被 libcublas 检查：

- CUBLAS_LOGINFO_DBG - 将此环境变量设置为 1 表示开启日志记录（默认情况下日志记录是关闭的）。
- CUBLAS_LOGDEST_DBG - 此环境变量指定日志写入位置：stdout、stderr 分别表示将日志消息写入标准输出或标准错误流。其他值会被解释为文件名。

**参数**

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| logIsOn | 主机端 | 输入 | 完全开启/关闭日志记录。默认关闭，但通过调用 cublasSetLoggerCallback() 设置用户定义的回调函数后会开启。 |
| logToStdOut | 主机端 | 输入 | 开启/关闭向标准输出 I/O 流的日志记录。默认关闭。 |
| logToStdErr | 主机端 | 输入 | 开启/关闭向标准错误 I/O 流的日志记录。默认关闭。 |
| logFileName | 主机端 | 输入 | 开启/关闭向由其名称指定的文件系统中的文件的日志记录。cublasLoggerConfigure() 会复制 logFileName 的内容。如果不需要此类型的日志记录，应提供空指针。 |

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |