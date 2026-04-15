### 3.1.2. 启发式缓存 (Heuristics Cache)

cuBLASLt 使用启发式算法根据问题规模、GPU 配置和其他参数选择最合适的矩阵乘法内核来执行。这需要在主机 CPU 上执行一些计算，可能需要几十微秒。为了克服这个开销，建议使用 `cublasLtMatmulAlgoGetHeuristic()` 查询一次启发式算法，然后复用该结果进行后续的 `cublasLtMatmul()` 计算。

对于无法一次性查询并复用启发式算法的情况，cuBLASLt 实现了一个启发式缓存，该缓存将矩阵乘法问题映射到之前由启发式算法选择过的内核。启发式缓存使用类 LRU（最近最少使用）驱逐策略，并且是线程安全的。

用户可以通过 `CUBLASLT_HEURISTICS_CACHE_CAPACITY` 环境变量或 `cublasLtHeuristicsCacheSetCapacity()` 函数来控制启发式缓存的容量，后者具有更高的优先级。容量以条目数量衡量，可能会因为性能原因向上取整到某个因子的倍数。每个条目大约占用 360 字节，但可能会有所变化。默认容量为 8192 条。

> **注意**

将容量设置为零会完全禁用缓存。这对于没有稳定状态的工作负载很有用，在这种情况下缓存操作的开销可能高于常规启发式计算。

> **注意**

出于性能原因，缓存并非最优的，因此有时需要将容量增加 1.5 倍到 2 倍以上，以达到预期的唯一矩阵乘法问题数量，从而获得接近完美的命中率。

另请参阅：`cublasLtHeuristicsCacheGetCapacity()`、`cublasLtHeuristicsCacheSetCapacity()`。