### 3.4.9. cublasLtHeuristicsCacheSetCapacity()

```c++
cublasStatus_t cublasLtHeuristicsCacheSetCapacity(size_t capacity);
```

设置启发式缓存的容量。将容量设置为0以禁用启发式缓存。

此函数的优先级高于 `CUBLASLT_HEURISTICS_CACHE_CAPACITY` 环境变量。

**参数：**

| 参数 | 描述 |
| --- | --- |
| capacity | 期望的启发式缓存容量。 |

**返回值：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 容量设置成功。 |