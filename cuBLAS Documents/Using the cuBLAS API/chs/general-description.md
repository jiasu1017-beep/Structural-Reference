

## 2.1. General Description


This section describes how to use the cuBLAS library API.




######### 2.1.8. Cache Configuration
####### 2.1.7. Batching Kernels
##### 2.1.1. Error Status
##### 2.1.2. cuBLAS Context
##### 2.1.3. Thread Safety
##### 2.1.4. Results Reproducibility
##### 2.1.5. Scalar Parameters
##### 2.1.6. Parallelism with Streams
##### 2.1.7. Batching Kernels
##### 2.1.8. Cache Configuration
##### 2.1.9. Static Library Support
##### 2.1.10. GEMM Algorithms Numerical Behavior
##### 2.1.11. Tensor Core Usage
##### 2.1.12. CUDA Graphs Support
##### 2.1.13. 64-bit Integer Interface
##### 2.2.1. cublasHandle_t
##### 2.2.2. cublasStatus_t
##### 2.2.3. cublasOperation_t
##### 2.2.4. cublasFillMode_t
##### 2.2.5. cublasDiagType_t
##### 2.2.6. cublasSideMode_t
##### 2.2.7. cublasPointerMode_t
##### 2.2.8. cublasAtomicsMode_t
##### 2.2.9. cublasGemmAlgo_t
##### 2.2.10. cublasMath_t
##### 2.2.11. cublasComputeType_t
##### 2.2.12. cublasEmulationStrategy_t
##### 2.3.1. cudaDataType_t
##### 2.3.2. cudaEmulationStrategy_t
##### 2.3.3. cudaEmulationMantissaControl_t
##### 2.3.4. cudaEmulationSpecialValuesSupport_t
##### 2.3.5. libraryPropertyType_t
##### 2.4.1. cublasCreate()
##### 2.4.2. cublasDestroy()
##### 2.4.3. cublasGetVersion()
##### 2.4.4. cublasGetProperty()
##### 2.4.5. cublasGetStatusName()
##### 2.4.6. cublasGetStatusString()
##### 2.4.7. cublasSetStream()
##### 2.4.8. cublasSetWorkspace()
##### 2.4.9. cublasGetStream()
##### 2.4.10. cublasGetPointerMode()
##### 2.4.11. cublasSetPointerMode()
##### 2.4.12. cublasSetVector()
##### 2.4.13. cublasGetVector()
##### 2.4.14. cublasSetMatrix()
##### 2.4.15. cublasGetMatrix()
##### 2.4.16. cublasSetVectorAsync()
##### 2.4.17. cublasGetVectorAsync()
##### 2.4.18. cublasSetMatrixAsync()
##### 2.4.19. cublasGetMatrixAsync()
##### 2.4.20. cublasSetAtomicsMode()
##### 2.4.21. cublasGetAtomicsMode()
##### 2.4.22. cublasSetMathMode()
##### 2.4.23. cublasGetMathMode()
##### 2.4.24. cublasSetSmCountTarget()
##### 2.4.25. cublasGetSmCountTarget()
##### 2.4.26. cublasSetEmulationStrategy()
##### 2.4.27. cublasGetEmulationStrategy()
##### 2.4.28. cublasGetEmulationSpecialValuesSupport()
##### 2.4.29. cublasSetEmulationSpecialValuesSupport()
##### 2.4.30. cublasGetFixedPointEmulationMantissaControl()
##### 2.4.31. cublasSetFixedPointEmulationMantissaControl()
##### 2.4.32. cublasGetFixedPointEmulationMaxMantissaBitCount()
##### 2.4.33. cublasSetFixedPointEmulationMaxMantissaBitCount()
##### 2.4.34. cublasGetFixedPointEmulationMantissaBitOffset()
##### 2.4.35. cublasSetFixedPointEmulationMantissaBitOffset()
##### 2.4.36. cublasGetFixedPointEmulationMantissaBitCountPointer()
##### 2.4.37. cublasSetFixedPointEmulationMantissaBitCountPointer()
##### 2.4.38. cublasLoggerConfigure()
##### 2.4.39. cublasGetLoggerCallback()
##### 2.4.40. cublasSetLoggerCallback()
##### 2.5.1. cublasI<t>amax()
##### 2.5.2. cublasI<t>amin()
##### 2.5.3. cublas<t>asum()
##### 2.5.4. cublas<t>axpy()
##### 2.5.5. cublas<t>copy()
##### 2.5.6. cublas<t>dot()
##### 2.5.7. cublas<t>nrm2()
##### 2.5.8. cublas<t>rot()
##### 2.5.9. cublas<t>rotg()
##### 2.5.10. cublas<t>rotm()
##### 2.5.11. cublas<t>rotmg()
##### 2.5.12. cublas<t>scal()
##### 2.5.13. cublas<t>swap()
##### 2.6.1. cublas<t>gbmv()
##### 2.6.2. cublas<t>gemv()
##### 2.6.3. cublas<t>ger()
##### 2.6.4. cublas<t>sbmv()
##### 2.6.5. cublas<t>spmv()
##### 2.6.6. cublas<t>spr()
##### 2.6.7. cublas<t>spr2()
##### 2.6.8. cublas<t>symv()
##### 2.6.9. cublas<t>syr()
##### 2.6.10. cublas<t>syr2()
##### 2.6.11. cublas<t>tbmv()
##### 2.6.12. cublas<t>tbsv()
##### 2.6.13. cublas<t>tpmv()
##### 2.6.14. cublas<t>tpsv()
##### 2.6.15. cublas<t>trmv()
##### 2.6.16. cublas<t>trsv()
##### 2.6.17. cublas<t>hemv()
##### 2.6.18. cublas<t>hbmv()
##### 2.6.19. cublas<t>hpmv()
##### 2.6.20. cublas<t>her()
##### 2.6.21. cublas<t>her2()
##### 2.6.22. cublas<t>hpr()
##### 2.6.23. cublas<t>hpr2()
##### 2.6.24. cublas<t>gemvBatched()
##### 2.6.25. cublas<t>gemvStridedBatched()
##### 2.7.1. cublas<t>gemm()
##### 2.7.2. cublas<t>gemm3m()
##### 2.7.3. cublas<t>gemmBatched()
##### 2.7.4. cublas<t>gemmStridedBatched()
##### 2.7.5. cublas<t>gemmGroupedBatched()
##### 2.7.6. cublas<t>symm()
##### 2.7.7. cublas<t>syrk()
##### 2.7.8. cublas<t>syr2k()
##### 2.7.9. cublas<t>syrkx()
##### 2.7.10. cublas<t>trmm()
##### 2.7.11. cublas<t>trsm()
##### 2.7.12. cublas<t>trsmBatched()
##### 2.7.13. cublas<t>hemm()
##### 2.7.14. cublas<t>herk()
##### 2.7.15. cublas<t>her2k()
##### 2.7.16. cublas<t>herkx()
##### 2.8.1. cublas<t>geam()
##### 2.8.2. cublas<t>dgmm()
##### 2.8.3. cublas<t>getrfBatched()
##### 2.8.4. cublas<t>getrsBatched()
##### 2.8.5. cublas<t>getriBatched()
##### 2.8.6. cublas<t>matinvBatched()
##### 2.8.7. cublas<t>geqrfBatched()
##### 2.8.8. cublas<t>gelsBatched()
##### 2.8.9. cublas<t>tpttr()
##### 2.8.10. cublas<t>trttp()
##### 2.8.11. cublas<t>gemmEx()
##### 2.8.12. cublasGemmEx()
##### 2.8.13. cublasGemmBatchedEx()
##### 2.8.14. cublasGemmStridedBatchedEx()
##### 2.8.15. cublasGemmGroupedBatchedEx()
##### 2.8.16. cublasCsyrkEx()
##### 2.8.17. cublasCsyrk3mEx()
##### 2.8.18. cublasCherkEx()
##### 2.8.19. cublasCherk3mEx()
##### 2.8.20. cublasNrm2Ex()
##### 2.8.21. cublasAxpyEx()
##### 2.8.22. cublasDotEx()
##### 2.8.23. cublasRotEx()
##### 2.8.24. cublasScalEx()
### 2.1.1. Error Status


All cuBLAS library function calls return the error status cublasStatus_t.





### 2.1.2. cuBLAS Context


The application must initialize a handle to the cuBLAS library context by calling the cublasCreate() function. Then, the handle is explicitly passed to every subsequent library function call. Once the application finishes using the library, it must call the function cublasDestroy() to release the resources associated with the cuBLAS library context.


This approach allows the user to explicitly control the library setup when using multiple host threads and multiple GPUs. For example, the application can use `cudaSetDevice()` to associate different devices with different host threads and in each of those host threads it can initialize a unique handle to the cuBLAS library context, which will use the particular device associated with that host thread. Then, the cuBLAS library function calls made with different handles will automatically dispatch the computation to different devices.


The device associated with a particular cuBLAS context is assumed to remain unchanged between the corresponding cublasCreate() and cublasDestroy() calls. In order for the cuBLAS library to use a different device in the same host thread, the application must set the new device to be used by calling `cudaSetDevice()` and then create another cuBLAS context, which will be associated with the new device, by calling cublasCreate(). When multiple devices are available, applications must ensure that the device associated with a given cuBLAS context is current (e.g. by calling `cudaSetDevice()`) before invoking cuBLAS functions with this context.


A cuBLAS library context is tightly coupled with the CUDA context that is current at the time of the cublasCreate() call. An application that uses multiple CUDA contexts is required to create a cuBLAS context per CUDA context and make sure the former never outlives the latter. Starting from version 12.8, cuBLAS detects if the underlying CUDA context is tied to a graphics context and follows the shared memory size limits that are set in such case.





### 2.1.3. Thread Safety


The library is thread safe and its functions can be called from multiple host threads, even with the same handle. When multiple threads share the same handle, extreme care needs to be taken when the handle configuration is changed because that change will affect potentially subsequent cuBLAS calls in all threads. It is even more true for the destruction of the handle. So it is not recommended that multiple thread share the same cuBLAS handle.


Additional considerations apply when the same handle is used from multiple threads with a user provided workspace. See cublasSetWorkspace() for details.





### 2.1.4. Results Reproducibility


By design, all cuBLAS API routines from a given toolkit version, generate the same bit-wise results at every run when executed on GPUs with the same architecture and the same number of SMs. However, bit-wise reproducibility is not guaranteed across toolkit versions because the implementation might differ due to some implementation changes.


This guarantee no longer holds when multiple CUDA streams are active or fixed-point emulation is used. If multiple concurrent streams are active, the library may optimize total performance by picking different internal implementations.


> **Note**

Note
The non-deterministic behavior of multi-stream execution is due to library optimizations in selecting internal workspace for the routines running in parallel streams. To avoid this effect user can either:

provide a separate workspace for each used stream using the cublasSetWorkspace() function, or
have one cuBLAS handle per stream, or
use cublasLtMatmul() instead of GEMM-family of functions and provide user owned workspace, or
set a debug environment variable CUBLAS_WORKSPACE_CONFIG to :16:8 (may limit overall performance) or :4096:8 (will increase library footprint in GPU memory by approximately 24MiB).

The non-deterministic behavior of fixed-point emulation is due to the large workspace memory requirements (see Fixed-Point Workspace Requirements for details).  This requires dynamically allocating memory with cudaMallocAsync() and allocation failures result in fallbacks to non-emulated routines. To avoid this effect, users can provide workspace via cublasSetWorkspace() to meet fixed-point emulation workspace requirements.


Any of those settings will allow for deterministic behavior even with multiple concurrent streams sharing a single cuBLAS handle.


This behavior is expected to change in a future release.


For some routines such as cublas<t>symv() and cublas<t>hemv(), an alternate significantly faster routine can be chosen using the routine cublasSetAtomicsMode(). In that case, the results are not guaranteed to be bit-wise reproducible because atomics are used for the computation.





### 2.1.5. Scalar Parameters


There are two categories of the functions that use scalar parameters :


- Functions that take alpha and/or beta parameters by reference on the host or the device as scaling factors, such as gemm.
- Functions that return a scalar result on the host or the device such as amax(), amin, asum(), rotg(), rotmg(), dot() and nrm2().


For the functions of the first category, when the pointer mode is set to `CUBLAS_POINTER_MODE_HOST`, the scalar parameters `alpha` and/or `beta` can be on the stack or allocated on the heap, shouldn’t be placed in managed memory. Underneath, the CUDA kernels related to those functions will be launched with the value of `alpha` and/or `beta`. Therefore if they were allocated on the heap, they can be freed just after the return of the call even though the kernel launch is asynchronous. When the pointer mode is set to `CUBLAS_POINTER_MODE_DEVICE`, `alpha` and/or `beta` must be accessible on the device and their values should not be modified until the kernel is done. Note that since `cudaFree()` does an implicit `cudaDeviceSynchronize()`, `cudaFree()` can still be called on `alpha` and/or `beta` just after the call but it would defeat the purpose of using this pointer mode in that case.


For the functions of the second category, when the pointer mode is set to `CUBLAS_POINTER_MODE_HOST`, these functions block the CPU, until the GPU has completed its computation and the results have been copied back to the Host. When the pointer mode is set to `CUBLAS_POINTER_MODE_DEVICE`, these functions return immediately. In this case, similar to matrix and vector results, the scalar result is ready only when execution of the routine on the GPU has completed. This requires proper synchronization in order to read the result from the host.


In either case, the pointer mode `CUBLAS_POINTER_MODE_DEVICE` allows the library functions to execute completely asynchronously from the Host even when `alpha` and/or `beta` are generated by a previous kernel. For example, this situation can arise when iterative methods for solution of linear systems and eigenvalue problems are implemented using the cuBLAS library.





### 2.1.6. Parallelism with Streams


If the application uses the results computed by multiple independent tasks, CUDA™ streams can be used to overlap the computation performed in these tasks.


The application can conceptually associate each stream with each task. In order to achieve the overlap of computation between the tasks, the user should create CUDA™ streams using the function `cudaStreamCreate()` and set the stream to be used by each individual cuBLAS library routine by calling cublasSetStream() just before calling the actual cuBLAS routine. Note that cublasSetStream() resets the user-provided workspace to the default workspace pool; see cublasSetWorkspace(). Then, the computation performed in separate streams would be overlapped automatically when possible on the GPU. This approach is especially useful when the computation performed by a single task is relatively small and is not enough to fill the GPU with work.


We recommend using the new cuBLAS API with scalar parameters and results passed by reference in the device memory to achieve maximum overlap of the computation when using streams.


A particular application of streams, batching of multiple small kernels, is described in the following section.





### 2.1.7. Batching Kernels


In this section, we explain how to use streams to batch the execution of small kernels. For instance, suppose that we have an application where we need to make many small independent matrix-matrix multiplications with dense matrices.


It is clear that even with millions of small independent matrices we will not be able to achieve the same *GFLOPS* rate as with a one large matrix. For example, a single $n \times n$ large matrix-matrix multiplication performs $n^{3}$ operations for $n^{2}$ input size, while 1024 $\frac{n}{32} \times \frac{n}{32}$ small matrix-matrix multiplications perform $1024\left( \frac{n}{32} \right)^{3} = \frac{n^{3}}{32}$ operations for the same input size. However, it is also clear that we can achieve a significantly better performance with many small independent matrices compared with a single small matrix.


The architecture family of GPUs allows us to execute multiple kernels simultaneously. Hence, in order to batch the execution of independent kernels, we can run each of them in a separate stream. In particular, in the above example we could create 1024 CUDA™ streams using the function `cudaStreamCreate()`, then preface each call to cublas<t>gemm() with a call to cublasSetStream() with a different stream for each of the matrix-matrix multiplications (note that cublasSetStream() resets user-provided workspace to the default workspace pool, see cublasSetWorkspace()). This will ensure that when possible the different computations will be executed concurrently. Although the user can create many streams, in practice it is not possible to have more than 32 concurrent kernels executing at the same time.





### 2.1.8. Cache Configuration


On some devices, L1 cache and shared memory use the same hardware resources. The cache configuration can be set directly with the CUDA Runtime function cudaDeviceSetCacheConfig. The cache configuration can also be set specifically for some functions using the routine cudaFuncSetCacheConfig. Please refer to the CUDA Runtime API documentation for details about the cache configuration settings.


Because switching from one configuration to another can affect kernels concurrency, the cuBLAS Library does not set any cache configuration preference and relies on the current setting. However, some cuBLAS routines, especially Level-3 routines, rely heavily on shared memory. Thus the cache preference setting might affect adversely their performance.





### 2.1.9. Static Library Support


The cuBLAS Library is also delivered in a static form as `libcublas_static.a` on Linux. The static cuBLAS library and all other static math libraries depend on a common thread abstraction layer library called `libculibos.a`.


For example, on Linux, to compile a small application using cuBLAS, against the dynamic library, the following command can be used:



```c++

nvcc myCublasApp.c  -lcublas  -o myCublasApp


```


Whereas to compile against the static cuBLAS library, the following command must be used:



```c++

nvcc myCublasApp.c  -lcublas_static   -lculibos -o myCublasApp


```


It is also possible to use the native Host C++ compiler. Depending on the Host operating system, some additional libraries like `pthread` or `dl` might be needed on the linking line. The following command on Linux is suggested :



```c++

g++ myCublasApp.c  -lcublas_static   -lculibos -lcudart_static -lpthread -ldl -I <cuda-toolkit-path>/include -L <cuda-toolkit-path>/lib64 -o myCublasApp


```


Note that in the latter case, the library `cuda` is not needed. The CUDA Runtime will try to open explicitly the `cuda` library if needed. In the case of a system which does not have the CUDA driver installed, this allows the application to gracefully manage this issue and potentially run if a CPU-only path is available.


Starting with release 11.2, using the typed functions instead of the extension functions (cublas**Ex()) helps in reducing the binary size when linking to static cuBLAS Library.





### 2.1.10. GEMM Algorithms Numerical Behavior


Some GEMM algorithms split the computation along the dimension K to increase the GPU occupancy, especially when the dimension K is large compared to dimensions M and N. When this type of algorithm is chosen by the cuBLAS heuristics or explicitly by the user, the results of each split is summed deterministically into the resulting matrix to get the final result.


For the routines cublas<t>gemmEx() and cublasGemmEx(), when the compute type is greater than the output type, the sum of the split chunks can potentially lead to some intermediate overflows thus producing a final resulting matrix with some overflows. Those overflows might not have occurred if all the dot products had been accumulated in the compute type before being converted at the end in the output type. This computation side-effect can be easily exposed when the computeType is `CUDA_R_32F` and Atype, Btype and Ctype are `CUDA_R_16F`. This behavior can be controlled using the compute precision mode `CUBLAS_MATH_DISALLOW_REDUCED_PRECISION_REDUCTION` with cublasSetMathMode()





### 2.1.11. Tensor Core Usage


Tensor cores were first introduced with Volta GPUs (compute capability 7.0 and above) and significantly accelerate matrix multiplications. Starting with cuBLAS version 11.0.0, the library may automatically make use of Tensor Core capabilities wherever possible, unless they are explicitly disabled by selecting pedantic compute modes in cuBLAS (see cublasSetMathMode(), cublasMath_t).


It should be noted that the library will pick a Tensor Core enabled implementation wherever it determines that it would provide the best performance.


The best performance when using Tensor Cores can be achieved when the matrix dimensions and pointers meet certain memory alignment requirements. Specifically, all of the following conditions must be satisfied to get the most performance out of Tensor Cores:


- ((op_A == CUBLAS_OP_N ? m : k) * AtypeSize) % 16 == 0
- ((op_B == CUBLAS_OP_N ? k : n) * BtypeSize) % 16 == 0
- (m * CtypeSize) % 16 == 0
- (lda * AtypeSize) % 16 == 0
- (ldb * BtypeSize) % 16 == 0
- (ldc * CtypeSize) % 16 == 0
- intptr_t(A) % 16 == 0
- intptr_t(B) % 16 == 0
- intptr_t(C) % 16 == 0


To conduct matrix multiplication with FP8 types (see 8-bit Floating Point Data Types (FP8) Usage), you must ensure that your matrix dimensions and pointers meet the optimal requirements listed above.  Aside from FP8, there are no longer any restrictions on matrix dimensions and memory alignments to use Tensor Cores (starting with cuBLAS version 11.0.0).





### 2.1.12. CUDA Graphs Support


cuBLAS routines can be captured in CUDA Graph stream capture without restrictions in most situations.


The exception are routines that output results into host buffers (e.g. cublas<t>dot() while pointer mode `CUBLAS_POINTER_MODE_HOST` is configured), as it enforces synchronization.


For input coefficients (such as `alpha`, `beta`) behavior depends on the pointer mode setting:


- In the case of CUBLAS(LT)_POINTER_MODE_HOST, coefficient values are captured in the graph.
- In the case of pointer modes with device pointers, coefficient value is accessed using the device pointer at the time of graph execution.


> **Note**

Note
When captured in CUDA Graph stream capture, cuBLAS routines can create memory nodes through the use of stream-ordered allocation APIs, cudaMallocAsync and cudaFreeAsync. However, as there is currently no support for memory nodes in child graphs or graphs launched from the device, attempts to capture cuBLAS routines in such scenarios may fail. To avoid this issue, use the cublasSetWorkspace() function to provide user-owned workspace memory.





### 2.1.13. 64-bit Integer Interface


cuBLAS version 12 introduced 64-bit integer capable functions. Each 64-bit integer function is equivalent to a 32-bit integer function with the following changes:


- The function name has _64 suffix.
- The dimension (problem size) data type changed from int to int64_t. Examples of dimension: m, n, and k.
- The leading dimension data type changed from int to int64_t. Examples of leading dimension: lda, ldb, and ldc.
- The vector increment data type changed from int to int64_t. Examples of vector increment: incx and incy.


For example, consider the following 32-bit integer functions:



```c++

cublasStatus_t cublasSetMatrix(int rows, int cols, int elemSize, const void *A, int lda, void *B, int ldb);
cublasStatus_t cublasIsamax(cublasHandle_t handle, int n, const float *x, int incx, int *result);
cublasStatus_t cublasSsyr(cublasHandle_t handle, cublasFillMode_t uplo, int n, const float *alpha, const float *x, int incx, float *A, int lda);


```


The equivalent 64-bit integer functions are:



```c++

cublasStatus_t cublasSetMatrix_64(int64_t rows, int64_t cols, int64_t elemSize, const void *A, int64_t lda, void *B, int64_t ldb);
cublasStatus_t cublasIsamax_64(cublasHandle_t handle, int64_t n, const float *x, int64_t incx, int64_t *result);
cublasStatus_t cublasSsyr_64(cublasHandle_t handle, cublasFillMode_t uplo, int64_t n, const float *alpha, const float *x, int64_t incx, float *A, int64_t lda);


```


Not every function has a 64-bit integer equivalent. For instance, cublasSetMathMode() doesn’t have any arguments that could meaningfully be `int64_t`. For documentation brevity, the 64-bit integer APIs are not explicitly listed, but only mentioned that they exist for the relevant functions.





cuBLAS 12版本引入了支持64位整数的函数。每个64位整数函数等效于32位整数函数，但有以下变化：

- 函数名添加`_64`后缀。
- 维度（问题大小）的数据类型从`int`更改为`int64_t`。维度的示例：`m`、`n`和`k`。
- 主维度的数据类型从`int`更改为`int64_t`。主维度的示例：`lda`、`ldb`和`ldc`。
- 向量增量的数据类型从`int`更改为`int64_t`。向量增量的示例：`incx`和`incy`。

例如，考虑以下32位整数函数：

```c++

cublasStatus_t cublasSetMatrix(int rows, int cols, int elemSize, const void *A, int lda, void *B, int ldb);
cublasStatus_t cublasIsamax(cublasHandle_t handle, int n, const float *x, int incx, int *result);
cublasStatus_t cublasSsyr(cublasHandle_t handle, cublasFillMode_t uplo, int n, const float *alpha, const float *x, int incx, float *A, int lda);


```

等效的64位整数函数为：

```c++

cublasStatus_t cublasSetMatrix_64(int64_t rows, int64_t cols, int64_t elemSize, const void *A, int64_t lda, void *B, int64_t ldb);
cublasStatus_t cublasIsamax_64(cublasHandle_t handle, int64_t n, const float *x, int64_t incx, int64_t *result);
cublasStatus_t cublasSsyr_64(cublasHandle_t handle, cublasFillMode_t uplo, int64_t n, const float *alpha, const float *x, int64_t incx, float *A, int64_t lda);


```

并非每个函数都有64位整数等效版本。例如，`cublasSetMathMode()`没有任何可以有意义地使用`int64_t`的参数。为简洁起见，本文档不再单独列出64位整数API，仅说明相关函数存在64位整数版本。

cuBLAS 例程在大多数情况下可以不受限制地通过 CUDA Graph 流捕获进行捕获。

例外情况是那些将结果输出到主机缓冲区的例程（例如，当配置了指针模式 `CUBLAS_POINTER_MODE_HOST` 时的 `cublas<t>dot()`），因为这些例程会强制同步。

对于输入系数（如 `alpha`、`beta`），行为取决于指针模式的设置：

- 在 CUBLAS(LT)_POINTER_MODE_HOST 的情况下，系数值在图中被捕获。
- 在使用设备指针的指针模式下，系数值在图执行时通过设备指针访问。

> **注意**

当在 CUDA Graph 流捕获中捕获时，cuBLAS 例程可以通过流顺序分配 API（`cudaMallocAsync` 和 `cudaFreeAsync`）创建内存节点。但是，由于当前不支持子图或从设备启动的图中的内存节点，因此在此类场景中捕获 cuBLAS 例程可能会失败。为避免此问题，请使用 `cublasSetWorkspace()` 函数提供用户拥有的工作区内存。

所有 cuBLAS 库函数调用都会返回错误状态 `cublasStatus_t`。

某些 GEMM 算法会沿着 K 维度分割计算以提高 GPU 占用率，特别是当 K 维度相对于 M 和 N 维度较大时。当 cuBLAS 启发式算法选择或用户显式选择这种类型的算法时，每个分割的结果会被确定性求和到结果矩阵中，以获得最终结果。

对于 `cublas<t>gemmEx()` 和 `cublasGemmEx()` 例程，当计算类型大于输出类型时，分块求和可能会导致一些中间溢出，从而产生包含溢出的最终结果矩阵。如果所有点积在最终转换为输出类型之前先在计算类型中进行累积，则这些溢出可能不会发生。当 computeType 为 `CUDA_R_32F` 且 Atype、Btype 和 Ctype 为 `CUDA_R_16F` 时，这种计算副作用很容易暴露。可以使用 `cublasSetMathMode()` 设置计算精度模式 `CUBLAS_MATH_DISALLOW_REDUCED_PRECISION_REDUCTION` 来控制此行为。

如果应用程序使用由多个独立任务计算的结果，则可以使用 CUDA™ 流来重叠这些任务中执行的计算。

应用程序可以在概念上将每个流与每个任务相关联。为了实现任务之间计算的重叠，用户应使用 `cudaStreamCreate()` 函数创建 CUDA™ 流，并在调用实际的 cuBLAS 库例程之前通过调用 cublasSetStream() 来设置每个单独的 cuBLAS 库例程要使用的流。请注意，cublasSetStream() 会将用户提供的 workspace 重置为默认的 workspace pool；请参阅 cublasSetWorkspace()。然后，分离流中执行的计算将在 GPU 上尽可能自动重叠。当单个任务执行的计算相对较小且不足以用工作填充 GPU 时，这种方法特别有用。

为了在使用流时实现计算的最大重叠，我们建议使用新的 cuBLAS API，其中标量参数和结果通过设备内存中的引用传递。

流的一个特定应用——多个小内核的批处理——将在下一节中描述。

使用标量参数的函数分为两类：

- **第一类**：通过主机或设备上的引用接收 alpha 和/或 beta 参数作为缩放因子的函数，例如 `gemm`。
- **第二类**：在主机或设备上返回标量结果的函数，例如 `amax()`、`amin()`、`asum()`、`rotg()`、`rotmg()`、`dot()` 和 `nrm2()`。

对于第一类函数，当指针模式设置为 `CUBLAS_POINTER_MODE_HOST` 时，标量参数 `alpha` 和/或 `beta` 可以分配在栈上或堆上，但不应放置在托管内存中。在底层，与这些函数相关的 CUDA 内核将使用 `alpha` 和/或 `beta` 的值启动。因此，如果它们分配在堆上，即使内核启动是异步的，也可以在调用返回后立即释放。当指针模式设置为 `CUBLAS_POINTER_MODE_DEVICE` 时，`alpha` 和/或 `beta` 必须在设备上可访问，并且在其值被修改之前内核必须已经完成。请注意，由于 `cudaFree()` 会隐式执行 `cudaDeviceSynchronize()`，因此在调用后仍然可以在 `alpha` 和/或 `beta` 上调用 `cudaFree()`，但这样做会违背使用此指针模式的初衷。

对于第二类函数，当指针模式设置为 `CUBLAS_POINTER_MODE_HOST` 时，这些函数会阻塞 CPU，直到 GPU 完成计算并将结果复制回主机。当指针模式设置为 `CUBLAS_POINTER_MODE_DEVICE` 时，这些函数会立即返回。在这种情况下，与矩阵和向量结果类似，标量结果只有在 GPU 上的例程执行完成后才可用。这需要适当的同步操作才能从主机读取结果。

无论哪种情况，指针模式 `CUBLAS_POINTER_MODE_DEVICE` 允许库函数完全异步执行，与主机无关，即使 `alpha` 和/或 `beta` 是由前一个内核生成的。例如，在使用 cuBLAS 库实现线性系统求解和特征值问题的迭代方法时，可能会出现这种情况。

cuBLAS 库也可以以静态库的形式提供，在 Linux 上为 `libcublas_static.a`。静态 cuBLAS 库及其他所有静态数学库都依赖于一个名为 `libculibos.a` 的通用线程抽象层库。

例如，在 Linux 上，要使用动态库编译一个使用 cuBLAS 的小应用程序，可以使用以下命令：

```c++
nvcc myCublasApp.c  -lcublas  -o myCublasApp
```

而要使用静态 cuBLAS 库进行编译，则必须使用以下命令：

```c++
nvcc myCublasApp.c  -lcublas_static   -lculibos -o myCublasApp
```

也可以使用本机 Host C++ 编译器。根据 Host 操作系统的不同，链接时可能需要一些额外的库，如 `pthread` 或 `dl`。在 Linux 上建议使用以下命令：

```c++
g++ myCublasApp.c  -lcublas_static   -lculibos -lcudart_static -lpthread -ldl -I <cuda-toolkit-path>/include -L <cuda-toolkit-path>/lib64 -o myCublasApp
```

请注意，在后一种情况下，不需要 `cuda` 库。CUDA 运行时将在需要时显式尝试打开 `cuda` 库。对于没有安装 CUDA 驱动的系统，这允许应用程序优雅地处理此问题，并可能在有 CPU-only 路径可用时运行。

从 11.2 版本开始，使用类型化函数（typed functions）而不是扩展函数（`cublas**Ex()`）有助于在链接到静态 cuBLAS 库时减小二进制文件大小。

Tensor Core 最初随 Volta GPU（计算能力 7.0 及以上）引入，能够显著加速矩阵乘法运算。从 cuBLAS 11.0.0 版本开始，库可以自动利用 Tensor Core 功能（除非通过在 cuBLAS 中选择严格计算模式明确禁用，参见 cublasSetMathMode()、cublasMath_t）。

需要注意的是，库会在确定能够提供最佳性能的情况下选择启用 Tensor Core 的实现。

使用 Tensor Core 时，若矩阵维度和指针满足特定的内存对齐要求，可以获得最佳性能。具体来说，必须满足以下所有条件才能从 Tensor Core 获得最佳性能：

- ((op_A == CUBLAS_OP_N ? m : k) * AtypeSize) % 16 == 0
- ((op_B == CUBLAS_OP_N ? k : n) * BtypeSize) % 16 == 0
- (m * CtypeSize) % 16 == 0
- (lda * AtypeSize) % 16 == 0
- (ldb * BtypeSize) % 16 == 0
- (ldc * CtypeSize) % 16 == 0
- intptr_t(A) % 16 == 0
- intptr_t(B) % 16 == 0
- intptr_t(C) % 16 == 0

使用 FP8 类型进行矩阵乘法（参见 8 位浮点数据类型 (FP8) 使用），必须确保矩阵维度和指针满足上述最优要求。除 FP8 外，使用 Tensor Core 不再有矩阵维度和内存对齐的限制（从 cuBLAS 11.0.0 版本开始）。

该库是线程安全的，其函数可以从多个主机线程调用，即使使用相同的句柄。当多个线程共享同一个句柄时，在更改句柄配置时需要格外小心，因为该更改可能会影响所有线程中后续的 cuBLAS 调用。对于句柄的销毁更是如此。因此，不建议多个线程共享同一个 cuBLAS 句柄。

当同一句柄用于多个线程且用户提供工作空间时，需要额外注意。详见 `cublasSetWorkspace()`。