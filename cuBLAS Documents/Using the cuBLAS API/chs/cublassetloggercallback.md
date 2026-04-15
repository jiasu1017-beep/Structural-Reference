### 2.4.40. cublasSetLoggerCallback()

```c++

cublasStatus_t cublasSetLoggerCallback(
    cublasLogCallback   userCallback)


```

此函数通过 cuBLAS C 公共 API 安装用户自定义的回调函数。

| 参数 | 内存 | 输入/输出 | 含义 |
| --- | --- | --- | --- |
| userCallback | 主机 | 输入 | 指向用户定义的回调函数的指针。 |

| 错误值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |