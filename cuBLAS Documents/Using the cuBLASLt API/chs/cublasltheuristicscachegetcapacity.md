### 3.4.8. cublasLtHeuristicsCacheGetCapacity()

```c++
cublasStatus_t cublasLtHeuristicsCacheGetCapacity(size_t* capacity);
```

返回启发式缓存容量。

**参数：**

| 参数 | 描述 |
| --- | --- |
| capacity | 返回容量值的指针。 |

**返回值：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 容量已成功写入。 |
| CUBLAS_STATUS_INVALID_VALUE | 容量已成功设置。 |