### 3.4.6. cublasLtGetStatusName()

```c++
const char* cublasLtGetStatusName(cublasStatus_t status);
// 返回给定状态的字符串表示
```

返回给定状态的字符串表示。

**参数：** `cublasStatus_t` - 状态。

**返回：** `const char*` - 空字符终止的字符串。