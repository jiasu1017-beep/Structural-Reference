### 3.4.7. cublasLtGetStatusString()

```c++

const char* cublasLtGetStatusString(cublasStatus_t status);


```

返回给定状态的描述字符串。

**参数：** cublasStatus_t - 状态。

**返回值：** `const char*` - 以 NULL 结尾的字符串。