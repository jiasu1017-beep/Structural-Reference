### 3.4.5. cublasLtGetProperty()

```c++
cublasStatus_t cublasLtGetProperty(libraryPropertyType type, int *value);
```

此函数通过将请求的属性的值写入 `value` 参数所指向的内存位置来返回该属性的值。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| type |  | 输入 | `libraryPropertyType` 类型的值，用于请求属性。请参阅 `libraryPropertyType_t`。 |
| value |  | 输出 | 指向主机内存位置的指针，请求的信息应写入该位置。 |

**返回**：

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 请求的 `libraryPropertyType` 信息已成功写入指定地址。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 type 输入参数的值无效，或 `value` 为 NULL |

请参阅 `cublasStatus_t` 获取有效返回代码的完整列表。