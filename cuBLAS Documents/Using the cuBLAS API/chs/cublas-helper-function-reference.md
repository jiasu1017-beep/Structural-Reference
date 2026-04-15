## 2.4. cuBLAS 辅助函数参考



### 2.4.1. cublasCreate()



```c++

cublasStatus_t
cublasCreate(cublasHandle_t *handle)


```


此函数初始化 cuBLAS 库，并创建一个指向保存 cuBLAS 库上下文的不透明结构的句柄。它在主机和设备上分配硬件资源，必须在任何其他 cuBLAS 库调用之前调用。


cuBLAS 库上下文绑定到当前 CUDA 设备。要在多个设备上使用该库，需要为每个设备创建一个 cuBLAS 句柄。另请参阅 cuBLAS 上下文。


对于给定的设备，可以创建具有不同配置的多个 cuBLAS 句柄。对于从不同线程使用同一设备的多线程应用程序，推荐的编程模型是为每个线程创建一个 cuBLAS 句柄，并在整个线程生命周期内使用该 cuBLAS 句柄。


由于 `cublasCreate()` 分配一些内部资源，而通过调用 `cublasDestroy()` 释放这些资源将隐式调用 `cudaDeviceSynchronize()`，因此建议尽量减少调用这些函数的次数。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 初始化成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | CUDA™ 运行时初始化失败 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配资源 |
| CUBLAS_STATUS_INVALID_VALUE | handle 为 NULL |





### 2.4.2. cublasDestroy()



```c++

cublasStatus_t
cublasDestroy(cublasHandle_t handle)


```


此函数释放 cuBLAS 库使用的硬件资源。此函数通常是与特定句柄的 cuBLAS 库的最后一次调用。由于 `cublasCreate()` 分配一些内部资源，而通过调用 `cublasDestroy()` 释放这些资源将隐式调用 `cudaDeviceSynchronize()`，因此建议尽量减少调用这些函数的次数。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 关闭成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |





### 2.4.3. cublasGetVersion()



```c++

cublasStatus_t
cublasGetVersion(cublasHandle_t handle, int *version)


```


此函数返回 cuBLAS 库的版本号。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | version 为 NULL |


> **注意**

注意
此函数可以安全地使用设置为 NULL 的 handle 调用。这允许用户在不需要句柄的情况下获取库版本。另一种方法是使用 `cublasGetProperty()`。





### 2.4.4. cublasGetProperty()



```c++

cublasStatus_t
cublasGetProperty(libraryPropertyType type, int *value)


```


此函数返回 value 指向的内存中请求属性的值。请参阅 `libraryPropertyType` 了解支持的类型。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | type 无效或 value 为 NULL |





### 2.4.5. cublasGetStatusName()



```c++

const char* cublasGetStatusName(cublasStatus_t status)


```


此函数返回给定状态的字符串表示形式。


| 返回值 | 含义 |
| --- | --- |
| NULL 终止字符串 | 状态的字符串表示形式 |





### 2.4.6. cublasGetStatusString()



```c++

const char* cublasGetStatusString(cublasStatus_t status)


```


此函数返回给定状态的描述字符串。


| 返回值 | 含义 |
| --- | --- |
| NULL 终止字符串 | 状态的描述 |





### 2.4.7. cublasSetStream()



```c++

cublasStatus_t
cublasSetStream(cublasHandle_t handle, cudaStream_t streamId)


```


此函数设置 cuBLAS 库流，该流将用于执行所有后续的 cuBLAS 库函数调用。如果未设置 cuBLAS 库流，所有内核将使用默认的 NULL 流。特别地，此例程可用于在内核启动之间更改流，然后重置 cuBLAS 库流回 NULL。此外，此函数无条件地将 cuBLAS 库工作空间重置回默认工作空间池（请参阅 `cublasSetWorkspace()`）。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 流设置成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |





### 2.4.8. cublasSetWorkspace()



```c++

cublasStatus_t
cublasSetWorkspace(cublasHandle_t handle, void *workspace, size_t workspaceSizeInBytes)


```


此函数将 cuBLAS 库工作空间设置为用户拥有的设备缓冲区，该缓冲区将用于执行所有后续的 cuBLAS 库函数调用（在当前设置的流上）。如果未设置 cuBLAS 库工作空间，所有内核将使用在 cuBLAS 上下文创建期间分配的默认工作空间池。特别地，此例程可用于在内核启动之间更改工作空间。工作空间指针必须至少对齐 256 字节，否则将返回 `CUBLAS_STATUS_INVALID_VALUE` 错误。`cublasSetStream()` 函数无条件地将 cuBLAS 库工作空间重置回默认工作空间池。调用此函数（包括将 `workspaceSizeInBytes` 设置为 0）将阻止 cuBLAS 库使用默认工作空间。`workspaceSizeInBytes` 值太小可能导致某些例程失败并返回 `CUBLAS_STATUS_ALLOC_FAILED` 错误，或导致性能大幅下降。工作空间大小等于或大于 16 KiB 就足以防止 `CUBLAS_STATUS_ALLOC_FAILED` 错误，而更大的工作空间可以为某些例程提供性能优势。


> **注意**

注意
如果 `cublasSetStream()` 设置的流是 `cudaStreamPerThread`，并且有多个线程使用同一个 cuBLAS 库句柄，则用户必须手动管理同步以避免用户提供的工作空间中可能的竞争条件。另一种选择是依赖默认工作空间池，它能安全地防止竞争条件。


> **警告**

警告
cuBLAS 函数可能调用多个 CUDA 内核，并依赖工作空间在调用之间保持不变。因此，如果 cuBLAS 句柄配置了用户提供的工作空间并从多个线程使用，则用户有责任在线程之间序列化 cuBLAS 调用，否则来自不同 cuBLAS 调用的内核可能会交错并使它们对工作空间完整性的假设无效。cuBLAS 管理的默认工作空间池是线程安全的。


下表显示了用户提供的工作空间的推荐大小。
这是基于 cuBLAS 默认工作空间池大小，该大小取决于 GPU 架构。


| GPU 架构 | 推荐工作空间大小 |
| --- | --- |
| NVIDIA Hopper 架构 (sm90) | 32 MiB |
| NVIDIA Blackwell 架构 (sm10x) | 32 MiB |
| NVIDIA Blackwell 架构 (sm12x) | 32 MiB |
| 其他 | 4 MiB |


> **注意**

注意
如果 cuBLAS 库配置为使用定点仿真（可以通过在 `cublasSetMathMode()` 中设置相应的数学模式或使用 `CUBLAS_COMPUTE_64F_EMULATED_FIXEDPOINT` 调用 API 来完成），则提供比 GPU 架构推荐值更多的工作空间可能是有益的。有关更多详细信息，请参阅定点工作空间要求。


此函数返回的可能错误值及其含义如下所列。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 流设置成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 工作空间指针未对齐到至少 256 字节 |





### 2.4.9. cublasGetStream()



```c++

cublasStatus_t
cublasGetStream(cublasHandle_t handle, cudaStream_t *streamId)


```


此函数获取正在用于执行所有 cuBLAS 库函数调用的 cuBLAS 库流。如果未设置 cuBLAS 库流，所有内核将使用默认的 NULL 流。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 流成功返回 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | streamId 为 NULL |





### 2.4.10. cublasGetPointerMode()



```c++

cublasStatus_t
cublasGetPointerMode(cublasHandle_t handle, cublasPointerMode_t *mode)


```


此函数获取 cuBLAS 库使用的指针模式。请参阅 `cublasPointerMode_t` 类型部分了解更多详情。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 指针模式成功获取 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | mode 为 NULL |





### 2.4.11. cublasSetPointerMode()



```c++

cublasStatus_t
cublasSetPointerMode(cublasHandle_t handle, cublasPointerMode_t mode)


```


此函数设置 cuBLAS 库使用的指针模式。默认值为在主机上通过引用传递值。请参阅 `cublasPointerMode_t` 类型部分了解更多详情。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 指针模式设置成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | mode 不是 CUBLAS_POINTER_MODE_HOST 或 CUBLAS_POINTER_MODE_DEVICE |





### 2.4.12. cublasSetVector()



```c++

cublasStatus_t
cublasSetVector(int n, int elemSize,
                const void *x, int incx, void *y, int incy)


```


此函数支持 64 位整数接口。


此函数将 `n` 个元素从主机内存空间中的向量 `x` 复制到 GPU 内存空间中的向量 `y`。假设两个向量中的每个元素的大小为 `elemSize` 字节。连续元素之间的存储间距由源向量 `x` 的 `incx` 和目标向量 `y` 的 `incy` 给出。


由于假设二维矩阵采用列主序格式，如果向量是矩阵的一部分，则等于 `1` 的向量增量访问该矩阵的（部分）列。类似地，使用等于矩阵主维的增量会访问该矩阵的（部分）行。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | incx、incy 或 elemSize 参数不为正 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时出错 |





### 2.4.13. cublasGetVector()



```c++

cublasStatus_t
cublasGetVector(int n, int elemSize,
                const void *x, int incx, void *y, int incy)


```


此函数支持 64 位整数接口。


此函数将 `n` 个元素从 GPU 内存空间中的向量 `x` 复制到主机内存空间中的向量 `y`。假设两个向量中的每个元素的大小为 `elemSize` 字节。连续元素之间的存储间距由源向量的 `incx` 和目标向量 `y` 的 `incy` 给出。


由于假设二维矩阵采用列主序格式，如果向量是矩阵的一部分，则等于 `1` 的向量增量访问该矩阵的（部分）列。类似地，使用等于矩阵主维的增量会访问该矩阵的（部分）行。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | incx、incy 或 elemSize 参数不为正 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时出错 |





### 2.4.14. cublasSetMatrix()



```c++

cublasStatus_t
cublasSetMatrix(int rows, int cols, int elemSize,
                const void *A, int lda, void *B, int ldb)


```


此函数支持 64 位整数接口。


此函数将 `rows x cols` 个元素的块从主机内存空间中的矩阵 `A` 复制到 GPU 内存空间中的矩阵 `B`。假设每个元素需要 `elemSize` 字节的存储空间，并且两个矩阵都以列主序格式存储，源矩阵 `A` 和目标矩阵 `B` 的主维分别由 `lda` 和 `ldb` 给出。主维表示已分配矩阵的行数，即使只使用其子矩阵。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | rows 或 cols 参数为负，或 elemSize、lda、ldb 不为正 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时出错 |





### 2.4.15. cublasGetMatrix()



```c++

cublasStatus_t
cublasGetMatrix(int rows, int cols, int elemSize,
                const void *A, int lda, void *B, int ldb)


```


此函数支持 64 位整数接口。


此函数将 `rows x cols` 个元素的块从 GPU 内存空间中的矩阵 `A` 复制到主机内存空间中的矩阵 `B`。假设每个元素需要 `elemSize` 字节的存储空间，并且两个矩阵都以列主序格式存储，源矩阵 `A` 和目标矩阵 `B` 的主维分别由 `lda` 和 `ldb` 给出。主维表示已分配矩阵的行数，即使只使用其子矩阵。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | rows 或 cols 参数为负，或 elemSize、lda、ldb 不为正 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时出错 |





### 2.4.16. cublasSetVectorAsync()



```c++

cublasStatus_t
cublasSetVectorAsync(int n, int elemSize, const void *hostPtr, int incx,
                     void *devicePtr, int incy, cudaStream_t stream)


```


此函数支持 64 位整数接口。


此函数具有与 `cublasSetVector()` 相同的功能，不同之处在于使用给定的 CUDA™ 流参数异步（相对于主机）进行数据传输。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | incx、incy 或 elemSize 参数不为正 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时出错 |





### 2.4.17. cublasGetVectorAsync()



```c++

cublasStatus_t
cublasGetVectorAsync(int n, int elemSize, const void *devicePtr, int incx,
                     void *hostPtr, int incy, cudaStream_t stream)


```


此函数支持 64 位整数接口。


此函数具有与 `cublasGetVector()` 相同的功能，不同之处在于使用给定的 CUDA™ 流参数异步（相对于主机）进行数据传输。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | incx、incy 或 elemSize 参数不为正 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时出错 |





### 2.4.18. cublasSetMatrixAsync()



```c++

cublasStatus_t
cublasSetMatrixAsync(int rows, int cols, int elemSize, const void *A,
                     int lda, void *B, int ldb, cudaStream_t stream)


```


此函数支持 64 位整数接口。


此函数具有与 `cublasSetMatrix()` 相同的功能，不同之处在于使用给定的 CUDA™ 流参数异步（相对于主机）进行数据传输。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | rows 或 cols 参数为负，或 elemSize、lda、ldb 不为正 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时出错 |





### 2.4.19. cublasGetMatrixAsync()



```c++

cublasStatus_t
cublasGetMatrixAsync(int rows, int cols, int elemSize, const void *A,
                     int lda, void *B, int ldb, cudaStream_t stream)


```


此函数支持 64 位整数接口。


此函数具有与 `cublasGetMatrix()` 相同的功能，不同之处在于使用给定的 CUDA™ 流参数异步（相对于主机）进行数据传输。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | rows 或 cols 参数为负，或 elemSize、lda、ldb 不为正 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时出错 |





### 2.4.20. cublasSetAtomicsMode()



```c++

cublasStatus_t cublasSetAtomicsMode(cublasHandlet handle, cublasAtomicsMode_t mode)


```


某些例程（如 `cublas<t>symv()` 和 `cublas<t>hemv()`）具有使用原子操作累积结果的替代实现。此实现通常显著更快，但可能产生每次运行不完全相同的结果。从数学上讲，这些不同结果并不重要，但在调试时这些差异可能是有害的。


此函数允许或禁止在所有具有替代实现的 cuBLAS 库例程中使用原子操作。当在任何 cuBLAS 例程的文档中未明确指定时，这意味着该例程没有使用原子操作的替代实现。禁用原子模式时，每个 cuBLAS 例程在使用相同参数在同一硬件上调用时应产生与另一次运行相同的结果。


默认原子模式下默认初始化的 `cublasHandle_t` 对象为 `CUBLAS_ATOMICS_NOT_ALLOWED`。请参阅该类型部分了解更多详情。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 原子模式设置成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |





### 2.4.21. cublasGetAtomicsMode()



```c++

cublasStatus_t cublasGetAtomicsMode(cublasHandle_t handle, cublasAtomicsMode_t *mode)


```


此函数查询特定 cuBLAS 上下文的原子模式。


默认原子模式下默认初始化的 `cublasHandle_t` 对象为 `CUBLAS_ATOMICS_NOT_ALLOWED`。请参阅该类型部分了解更多详情。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 原子模式查询成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | mode 参数为 NULL 指针 |





### 2.4.22. cublasSetMathMode()



```c++

cublasStatus_t cublasSetMathMode(cublasHandle_t handle, cublasMath_t mode)


```


`cublasSetMathMode()` 函数使您能够选择由 `cublasMath_t` 定义的计算精度模式。用户可以将其设置为逻辑组合（除了已弃用的 `CUBLAS_TENSOR_OP_MATH`）。例如，`cublasSetMathMode(handle, CUBLAS_DEFAULT_MATH | CUBLAS_MATH_DISALLOW_REDUCED_PRECISION_REDUCTION)`。请注意，默认数学模式为 `CUBLAS_DEFAULT_MATH`。


有关 `cublasGemmEx()` 和 `cublasLtMatmul()` API 及其步幅变体支持的矩阵和计算精度，请参阅：cublasGemmEx()、cublasGemmBatchedEx()、cublasGemmStridedBatchedEx() 和 cublasLtMatmul()。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 数学模式设置成功 |
| CUBLAS_STATUS_INVALID_VALUE | 指定了 mode 的无效值 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |





### 2.4.23. cublasGetMathMode()



```c++

cublasStatus_t cublasGetMathMode(cublasHandle_t handle, cublasMath_t *mode)


```


此函数返回库例程使用的数学模式。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 数学类型成功返回 |
| CUBLAS_STATUS_INVALID_VALUE | mode 为 NULL |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |





### 2.4.24. cublasSetSmCountTarget()



```c++

cublasStatus_t cublasSetSmCountTarget(cublasHandle_t handle, int smCountTarget)


```


`cublasSetSmCountTarget()` 函数允许覆盖内核执行期间库可用的多处理器数量。


当已知 cuBLAS 例程与其他工作同时在不同 CUDA 流上运行时，可以使用此选项来提高库性能。例如，在具有 108 个多处理器的 NVIDIA A100 GPU 上，当有并发内核以网格大小 8 运行时，可以使用 `cublasSetSmCountTarget()` 将 `smCountTarget` 设置为 `100`，以覆盖库启发式方法优化在剩余 100 个多处理器上运行。


设置为 `0` 时，库返回其默认行为。输入值不应超过设备的多处理器数量（可以使用 `cudaDeviceGetAttribute` 获取）。不接受负值。


用户必须确保使用此例程修改库句柄时的线程安全性，类似于使用 `cublasSetStream()` 等。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | SM 计数目标设置成功 |
| CUBLAS_STATUS_INVALID_VALUE | smCountTarget 值超出允许范围 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |





### 2.4.25. cublasGetSmCountTarget()



```c++

cublasStatus_t cublasGetSmCountTarget(cublasHandle_t handle, int *smCountTarget)


```


此函数获取先前编程到库句柄的值。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | SM 计数目标成功返回 |
| CUBLAS_STATUS_INVALID_VALUE | smCountTarget 为 NULL |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |





### 2.4.26. cublasSetEmulationStrategy()



```c++

cublasStatus_t cublasSetEmulationStrategy(cublasHandle_t handle, cublasEmulationStrategy_t emulationStrategy)


```


`cublasSetEmulationStrategy()` 函数使您能够选择库应如何利用浮点仿真。更多详情请参阅 `cublasEmulationStrategy_t`。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 仿真策略设置成功 |
| CUBLAS_STATUS_INVALID_VALUE | 指定了仿真策略的无效值 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |





### 2.4.27. cublasGetEmulationStrategy()



```c++

cublasStatus_t cublasGetEmulationStrategy(cublasHandle_t handle, cublasEmulationStrategy_t *emulationStrategy)


```


此函数获取先前编程到库句柄的值。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 仿真策略成功返回 |
| CUBLAS_STATUS_INVALID_VALUE | emulationStrategy 为 NULL |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |





### 2.4.28. cublasGetEmulationSpecialValuesSupport()



```c++

cublasStatus_t cublasGetEmulationSpecialValuesSupport(cublasHandle_t handle, cudaEmulationSpecialValuesSupport *mask)


```


此函数获取先前编程到库句柄的值。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 仿真特殊值支持成功返回 |
| CUBLAS_STATUS_INVALID_VALUE | mask 为 NULL |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |





### 2.4.29.

```c++
cublasStatus_t
cublasCreate(cublasHandle_t *handle)
```

此函数初始化 cuBLAS 库并创建一个指向包含 cuBLAS 库上下文的不透明结构的句柄。它在主机和设备上分配硬件资源，必须在其他任何 cuBLAS 库调用之前调用。

cuBLAS 库上下文与当前 CUDA 设备绑定。要在多个设备上使用该库，需要为每个设备创建一个 cuBLAS 句柄。另请参阅 cuBLAS 上下文。

对于给定的设备，可以创建具有不同配置的多个 cuBLAS 句柄。对于从不同线程使用同一设备的多线程应用程序，推荐的编程模型是为每个线程创建一个 cuBLAS 句柄，并在该线程的整个生命周期内使用该 cuBLAS 句柄。

由于 `cublasCreate()` 会分配一些内部资源，而调用 `cublasDestroy()` 释放这些资源时将隐式调用 `cudaDeviceSynchronize()`，因此建议尽量减少调用这些函数的次数。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 初始化成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | CUDA™ Runtime 初始化失败 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配资源 |
| CUBLAS_STATUS_INVALID_VALUE | handle 为 NULL |



```c++

cublasStatus_t
cublasDestroy(cublasHandle_t handle)


```


This function releases hardware resources used by the cuBLAS library. This function is usually the last call with a particular handle to the cuBLAS library. Because cublasCreate() allocates some internal resources and the release of those resources by calling cublasDestroy() will implicitly call `cudaDeviceSynchronize()`, it is recommended to minimize the number of times these functions are called.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | the shut down succeeded |
| CUBLAS_STATUS_NOT_INITIALIZED | the library was not initialized |




```c++
cublasStatus_t cublasGetAtomicsMode(cublasHandle_t handle, cublasAtomicsMode_t *mode)
```

此函数查询特定 cuBLAS 上下文的原子模式。

默认初始化的 `cublasHandle_t` 对象的默认原子模式为 `CUBLAS_ATOMICS_NOT_ALLOWED`。请参阅类型部分了解更多详情。

| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 原子模式查询成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 mode 为空指针 |

```c++
cublasStatus_t cublasGetEmulationSpecialValuesSupport(cublasHandle_t handle, cudaEmulationSpecialValuesSupport *mask)
```

此函数获取之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 仿真特殊值支持已成功返回。 |
| CUBLAS_STATUS_INVALID_VALUE | mask 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

```c++
cublasStatus_t cublasGetEmulationStrategy(cublasHandle_t handle, cublasEmulationStrategy_t *emulationStrategy)
```

此函数获取之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 模拟策略返回成功。 |
| CUBLAS_STATUS_INVALID_VALUE | emulationStrategy 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

```c++
cublasStatus_t cublasGetFixedPointEmulationMantissaBitCountPointer(cublasHandle_t handle, int **mantissaBitCount)
```

此函数获取之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | mantissaBitCount 已成功返回。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaBitCount 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

```c++

cublasStatus_t cublasGetFixedPointEmulationMantissaBitOffset(cublasHandle_t handle, int *mantissaBitOffset)


```

此函数用于获取之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | mantissaBitOffset 已成功返回。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaBitOffset 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

```c++

cublasStatus_t cublasGetFixedPointEmulationMantissaControl(cublasHandle_t handle, cudaEmulationMantissaControl *mantissaControl)

```

此函数用于获取先前编程到库句柄的值。

| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 定点仿真尾数控制已成功返回。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaControl 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

```c++

cublasStatus_t cublasGetFixedPointEmulationMaxMantissaBitCount(cublasHandle_t handle, int *maxMantissaBitCount)

```

此函数获取先前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 成功返回 maxMantissaBitCount。 |
| CUBLAS_STATUS_INVALID_VALUE | maxMantissaBitCount 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

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

```c++
cublasStatus_t cublasGetMathMode(cublasHandle_t handle, cublasMath_t *mode)
// 此函数返回库例程使用的数学模式
```

此函数返回库例程使用的数学模式。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 数学类型已成功返回。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 mode 为 NULL。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

```c++
cublasStatus_t
cublasGetMatrix(int rows, int cols, int elemSize,
                const void *A, int lda, void *B, int ldb)
```

此函数支持64位整数接口。

此函数将`rows x cols`个元素组成的块从GPU内存空间中的矩阵`A`复制到主机内存空间中的矩阵`B`。假设每个元素需要`elemSize`字节的存储空间，且两个矩阵均以列主序格式存储，源矩阵`A`和目标矩阵`B`的前导维度分别由`lda`和`ldb`给出。前导维度表示已分配矩阵的行数，即使只使用其子矩阵也是如此。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数rows或cols为负，或elemSize、lda、ldb不为正数。 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问GPU内存时出错 |



```c++

cublasStatus_t
cublasGetMatrixAsync(int rows, int cols, int elemSize, const void *A,
                     int lda, void *B, int ldb, cudaStream_t stream)


```


This function supports the 64-bit Integer Interface.


This function has the same functionality as cublasGetMatrix(), with the exception that the data transfer is done asynchronously (with respect to the host) using the given CUDA™ stream parameter.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_INVALID_VALUE | The parameters rows or cols are negative, or elemSize, lda ldb are not positive. |
| CUBLAS_STATUS_MAPPING_ERROR | There was an error accessing GPU memory |




```c++
cublasStatus_t
cublasGetPointerMode(cublasHandle_t handle, cublasPointerMode_t *mode)
```

此函数用于获取cuBLAS库使用的指针模式。有关更多详细信息，请参阅关于`cublasPointerMode_t`类型的章节。

| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 指针模式获取成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | mode为NULL |

```c++

cublasStatus_t

cublasGetProperty(libraryPropertyType type, int *value)


```

此函数返回请求的属性的值，存储在 `value` 指向的内存中。请参阅 `libraryPropertyType` 了解支持的类型。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 类型或值无效，如果 `type` 的值无效，或如果 `value` 为 NULL |



```c++

cublasStatus_t cublasGetSmCountTarget(cublasHandle_t handle, int *smCountTarget)


```


This function obtains the value previously programmed to the library handle.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | SM count target was returned successfully. |
| CUBLAS_STATUS_INVALID_VALUE | smCountTarget is NULL. |
| CUBLAS_STATUS_NOT_INITIALIZED | the library was not initialized. |






```c++

const char* cublasGetStatusName(cublasStatus_t status)


```


此函数返回给定状态的字符串表示形式。


| 返回值 | 含义 |
| --- | --- |
| NULL-terminated string | 状态的字符串表示形式 |

```c++

const char* cublasGetStatusString(cublasStatus_t status)


```

此函数返回给定状态的描述字符串。

| 返回值 | 含义 |
| --- | --- |
| NULL 终止字符串 | 该状态的描述 |



```c++

cublasStatus_t
cublasGetStream(cublasHandle_t handle, cudaStream_t *streamId)


```


This function gets the cuBLAS library stream, which is being used to execute all calls to the cuBLAS library functions. If the cuBLAS library stream is not set, all kernels use the *default* NULL stream.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | the stream was returned successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | the library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | streamId is NULL |




```c++
cublasStatus_t
cublasGetVector(int n, int elemSize,
                const void *x, int incx, void *y, int incy)
```

此函数支持64位整数接口。

此函数将GPU内存空间中向量`x`的`n`个元素复制到主机内存空间中的向量`y`。两个向量中的元素都被假定为`elemSize`字节大小。源向量中连续元素之间的存储间距由`incx`给出，目标向量`y`的存储间距由`incy`给出。

由于假定二维矩阵采用列主序格式，如果向量是矩阵的一部分，则增量等于`1`会访问该矩阵的（部分）列。类似地，使用等于矩阵主维度的增量会访问该矩阵的（部分）行。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数incx、incy或elemSize不为正数 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问GPU内存时出错 |

```c++
cublasStatus_t
cublasGetVectorAsync(int n, int elemSize, const void *devicePtr, int incx,
                     void *hostPtr, int incy, cudaStream_t stream)
```

此函数支持 64 位整数接口。

此函数的功能与 `cublasGetVector()` 相同，区别在于数据传送是使用给定的 CUDA™ 流参数异步（相对于主机）完成的。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 incx、incy 或 elemSize 不为正数 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时出错 |



```c++

cublasStatus_t
cublasGetVersion(cublasHandle_t handle, int *version)


```


This function returns the version number of the cuBLAS library.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_INVALID_VALUE | version is NULL |


> **Note**

Note
This function can be safely called with handle set to NULL.  This allows users to get the version of the library without a handle.  Another way to do this is with cublasGetProperty().




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



```c++

cublasStatus_t cublasSetAtomicsMode(cublasHandlet handle, cublasAtomicsMode_t mode)


```


某些例程（如 `cublas<t>symv()` 和 `cublas<t>hemv()`）具有使用原子操作（atomics）累积结果的替代实现。这种实现通常速度明显更快，但可能在多次运行中产生不完全相同的结果。从数学角度来看，这些差异并不显著，但在调试时可能造成不利影响。


此函数允许或禁止在 cuBLAS 库中对所有具有替代实现的例程使用原子操作。如果在 cuBLAS 例程的文档中未明确说明，则表示该例程没有使用原子操作的替代实现。当禁用原子模式时，在同一硬件上使用相同参数调用时，每个 cuBLAS 例程应产生相同的结果。


默认初始化的 `cublasHandle_t` 对象的原子模式为 `CUBLAS_ATOMICS_NOT_ALLOWED`。请参阅类型部分了解更多详情。


| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 原子模式设置成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |

```c++

cublasStatus_t cublasSetEmulationSpecialValuesSupport(cublasHandle_t handle, cudaEmulationSpecialValuesSupport mask)


```

此函数设置之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 仿真特殊值支持已成功设置。 |
| CUBLAS_STATUS_INVALID_VALUE | mask 超出允许范围。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

```c++

cublasStatus_t cublasSetEmulationStrategy(cublasHandle_t handle, cublasEmulationStrategy_t emulationStrategy)


```

`cublasSetEmulationStrategy()` 函数使您能够选择库如何使用浮点模拟。更多详细信息，请参阅 `cublasEmulationStrategy_t`。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 模拟策略设置成功。 |
| CUBLAS_STATUS_INVALID_VALUE | 指定的模拟策略值无效。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

```c++
cublasStatus_t cublasSetFixedPointEmulationMantissaBitCountPointer(cublasHandle_t handle, int *mantissaBitCount)
```

此函数设置之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | mantissaBitCount 设置成功。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaBitCount 超出允许范围。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

```c++
cublasStatus_t cublasSetFixedPointEmulationMantissaBitOffset(cublasHandle_t handle, int mantissaBitOffset)
```

此函数用于设置之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | mantissaBitOffset 已成功设置。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaBitOffset 超出允许范围。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |

```c++
cublasStatus_t cublasSetFixedPointEmulationMantissaControl(cublasHandle_t handle, cudaEmulationMantissaControl mantissaControl)
```

此函数用于设置之前编程到库句柄的值。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 定点仿真尾数控制设置成功。 |
| CUBLAS_STATUS_INVALID_VALUE | mantissaControl 超出允许范围。 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化。 |



```c++

cublasStatus_t cublasSetFixedPointEmulationMaxMantissaBitCount(cublasHandle_t handle, int maxMantissaBitCount)


```


This function sets the value previously programmed to the library handle.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | maxMantissaBitCount was set successfully. |
| CUBLAS_STATUS_INVALID_VALUE | maxMantissaBitCount is outside of the allowed range. |
| CUBLAS_STATUS_NOT_INITIALIZED | the library was not initialized. |




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



```c++

cublasStatus_t cublasSetMathMode(cublasHandle_t handle, cublasMath_t mode)


```


The cublasSetMathMode() function enables you to choose the compute precision modes as defined by cublasMath_t. Users are allowed to set the compute precision mode as a logical combination of them (except the deprecated `CUBLAS_TENSOR_OP_MATH`). For example, `cublasSetMathMode(handle, CUBLAS_DEFAULT_MATH | CUBLAS_MATH_DISALLOW_REDUCED_PRECISION_REDUCTION)`. Please note that the default math mode is `CUBLAS_DEFAULT_MATH`.


For matrix and compute precisions allowed for cublasGemmEx() and cublasLtMatmul() APIs and their strided variants please refer to: cublasGemmEx() , cublasGemmBatchedEx(), cublasGemmStridedBatchedEx(), and cublasLtMatmul().


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The math mode was set successfully. |
| CUBLAS_STATUS_INVALID_VALUE | An invalid value for mode was specified. |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized. |




```c++
cublasStatus_t
cublasSetMatrix(int rows, int cols, int elemSize,
                const void *A, int lda, void *B, int ldb)
```

此函数支持64位整数接口。

此函数将主机内存空间中矩阵 `A` 的 `rows x cols` 个元素的数据块复制到GPU内存空间中的矩阵 `B`。该函数假定每个元素需要 `elemSize` 字节的存储空间，并且两个矩阵均以列优先格式存储。源矩阵 `A` 和目标矩阵 `B` 的主维分别由 `lda` 和 `ldb` 给出。主维表示已分配矩阵的行数，即使仅使用其中的子矩阵。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 rows 或 cols 为负，或者 elemSize、lda、ldb 不为正数 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问GPU内存时出错 |

```c++

cublasStatus_t
cublasSetMatrixAsync(int rows, int cols, int elemSize, const void *A,
                     int lda, void *B, int ldb, cudaStream_t stream)


```

此函数支持64位整数接口。

此函数的功能与 `cublasSetMatrix()` 相同，区别在于数据传送是通过给定的 CUDA™ 流参数异步执行的（相对于主机而言）。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数 `rows` 或 `cols` 为负数，或 `elemSize`、`lda`、`ldb` 不为正数。 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存时发生错误 |

```c++
cublasStatus_t
cublasSetPointerMode(cublasHandle_t handle, cublasPointerMode_t mode)
```

此函数设置 cuBLAS 库使用的指针模式。*默认*情况下，值通过主机上的引用传递。请参阅 cublasPointerMode_t 类型部分以了解更多详细信息。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 指针模式设置成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |
| CUBLAS_STATUS_INVALID_VALUE | mode 不是 CUBLAS_POINTER_MODE_HOST 或 CUBLAS_POINTER_MODE_DEVICE |



```c++

cublasStatus_t cublasSetSmCountTarget(cublasHandle_t handle, int smCountTarget)


```


The cublasSetSmCountTarget() function allows overriding the number of multiprocessors available to the library during kernels execution.


This option can be used to improve the library performance when cuBLAS routines are known to run concurrently with other work on different CUDA streams. For example, on an NVIDIA A100 GPU, which has 108 multiprocessors, when there is a concurrent kenrel running with grid size of 8, one can use cublasSetSmCountTarget() with `smCountTarget` set to `100` to override the library heuristics to optimize for running on the remaining 100 multiprocessors.


When set to `0`, the library returns to its default behavior. The input value should not exceed the device’s multiprocessor count, which can be obtained using `cudaDeviceGetAttribute`. Negative values are not accepted.


The user must ensure thread safety when modifying the library handle with this routine similar to when using cublasSetStream(), etc.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | SM count target was set successfully. |
| CUBLAS_STATUS_INVALID_VALUE | The value of smCountTarget outside of the allowed range. |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized. |




```c++
cublasStatus_t
cublasSetStream(cublasHandle_t handle, cudaStream_t streamId)
```

此函数用于设置 cuBLAS 库的流，后续对 cuBLAS 库函数的所有调用都将在此流中执行。如果未设置 cuBLAS 库的流，则所有内核将使用*默认*的 NULL 流。具体来说，此例程可用于在内核启动之间更改流，然后将 cuBLAS 库的流重置回 NULL。此外，此函数无条件地将 cuBLAS 库的工作空间重置回默认工作空间池（请参阅 cublasSetWorkspace()）。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 流设置成功 |
| CUBLAS_STATUS_NOT_INITIALIZED | 库未初始化 |



```c++

cublasStatus_t
cublasSetVector(int n, int elemSize,
                const void *x, int incx, void *y, int incy)


```


This function supports the 64-bit Integer Interface.


This function copies `n` elements from a vector `x` in host memory space to a vector `y` in GPU memory space. Elements in both vectors are assumed to have a size of `elemSize` bytes. The storage spacing between consecutive elements is given by `incx` for the source vector `x` and by `incy` for the destination vector `y`.


Since column-major format for two-dimensional matrices is assumed, if a vector is part of a matrix, a vector increment equal to `1` accesses a (partial) column of that matrix. Similarly, using an increment equal to the leading dimension of the matrix results in accesses to a (partial) row of that matrix.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_INVALID_VALUE | The parameters incx, incy, or elemSize are not positive |
| CUBLAS_STATUS_MAPPING_ERROR | There was an error accessing GPU memory |




```c++

cublasStatus_t
cublasSetVectorAsync(int n, int elemSize, const void *hostPtr, int incx,
                     void *devicePtr, int incy, cudaStream_t stream)


```

此函数支持64位整数接口。

此函数的功能与`cublasSetVector()`相同，不同之处在于数据传送是使用指定的CUDA™流参数异步执行的（相对于主机）。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数incx、incy或elemSize不为正数 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问GPU内存时出错 |



```c++

cublasStatus_t
cublasSetWorkspace(cublasHandle_t handle, void *workspace, size_t workspaceSizeInBytes)


```


This function sets the cuBLAS library workspace to a user-owned device buffer, which will be used to execute all subsequent calls to the cuBLAS library functions (on the currently set stream). If the cuBLAS library workspace is not set, all kernels will use the default workspace pool allocated during the cuBLAS context creation. In particular, this routine can be used to change the workspace between kernel launches. The workspace pointer has to be aligned to at least 256 bytes, otherwise `CUBLAS_STATUS_INVALID_VALUE` error is returned. The cublasSetStream() function unconditionally resets the cuBLAS library workspace back to the default workspace pool. Calling this function, including with `workspaceSizeInBytes` equal to 0, will prevent the cuBLAS library from utilizing the default workspace. Too small value of `workspaceSizeInBytes` may cause some routines to fail with `CUBLAS_STATUS_ALLOC_FAILED` error returned or cause large regressions in performance. Workspace size equal to or larger than 16KiB is enough to prevent `CUBLAS_STATUS_ALLOC_FAILED` error, while a larger workspace can provide performance benefits for some routines.


> **Note**

Note
If the stream set by cublasSetStream() is cudaStreamPerThread and there are multiple threads using the same cuBLAS library handle, then users must manually manage synchronization to avoid possible race conditions in the user provided workspace. Alternatively, users may rely on the default workspace pool which safely guards against race conditions.


> **Warning**

Warning
cuBLAS functions may invoke more than one CUDA kernel, and rely on workspace being intact between the invocations. Hence, if cuBLAS handle is configured with user-provided workspace and is being used from multiple threads, it is user’s responsibility to serialize cuBLAS calls between threads, as otherwise the kernels from different cuBLAS invocations might interleave and invalidate the assumptions each of them makes regarding workspace intactness. The default workspace pool managed by cuBLAS is thread safe.


The table below shows the recommended size of user-provided workspace.
This is based on the cuBLAS default workspace pool size which is GPU architecture dependent.


| GPU Architecture | Recommended workspace size |
| --- | --- |
| NVIDIA Hopper Architecture (sm90) | 32 MiB |
| NVIDIA Blackwell Architecture (sm10x) | 32 MiB |
| NVIDIA Blackwell Architecture (sm12x) | 32 MiB |
| Other | 4 MiB |


> **Note**

Note
If the cuBLAS library is configured to utilize fixed-point emulation, which can be done by setting the corresponding math mode in cublasSetMathMode() or calling APIs with CUBLAS_COMPUTE_64F_EMULATED_FIXEDPOINT, it can be beneficial to provide more workspace than recommended for the GPU architecture.  See Fixed-Point Workspace Requirements for more details.


The possible error values returned by this function and their meanings are listed below.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The stream was set successfully |
| CUBLAS_STATUS_NOT_INITIALIZED | The library was not initialized |
| CUBLAS_STATUS_INVALID_VALUE | The workspace pointer wasn’t aligned to at least 256 bytes |


