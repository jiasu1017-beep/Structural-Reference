### 2.4.39. cublasGetLoggerCallback()

```c++
cublasStatus_t cublasGetLoggerCallback(
    cublasLogCallback* userCallback)
```

此函数用于检索通过 `cublasSetLoggerCallback()` 安装的自定义用户回调函数的函数指针；如果未安装回调函数，则返回零。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| userCallback | host | output | 指向用户定义的回调函数的指针。 |

此函数返回的可能错误值及其含义如下所示。

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | userCallback 为 NULL |