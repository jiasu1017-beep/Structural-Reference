### 2.4.4. cublasGetProperty()

```c++

cublasStatus_t

cublasGetProperty(libraryPropertyType type, int *value)


```

此函数返回请求的属性的值，存储在 `value` 指向的内存中。请参阅 `libraryPropertyType` 了解支持的类型。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 类型或值无效，如果 `type` 的值无效，或如果 `value` 为 NULL |