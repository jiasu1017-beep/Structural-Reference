## 1.2. 新版和旧版 cuBLAS API

从 4.0 版本开始，cuBLAS 库除了现有的旧版 API 外，还提供了新的 API。本节讨论为何提供新 API、使用新 API 的优势，以及与现有旧版 API 的区别。

> **Warning**
>
> 警告
>
> 旧版 cuBLAS API 已弃用，将在未来的版本中移除。

可通过包含头文件 `cublas_v2.h` 来使用新的 cuBLAS 库 API。它具有旧版 cuBLAS API 不具备的以下特性：

- cuBLAS 库上下文的句柄使用函数初始化，并明确传递给每个后续的库函数调用。这允许用户在多个主机线程和多个 GPU 环境下对库设置拥有更多控制权。这也使 cuBLAS API 可重入。
- 标量 \(\alpha\) 和 \(\beta\) 可以通过引用传递给主机或设备，而不仅限于按值仅在主机上传递。此更改允许库函数即使在 \(\alpha\) 和 \(\beta\) 由前一个内核生成的情况下也能使用流异步执行。
- 当库例程返回标量结果时，可以通过引用返回给主机或设备，而不仅限于按值仅在主机上返回。此更改允许库例程在标量结果在设备上生成并通过引用返回时异步调用，从而实现最大并行性。
- 所有 cuBLAS 库函数调用都返回错误状态 `cublasStatus_t`。此更改便于调试并简化软件开发。注意，`cublasStatus` 已重命名为 `cublasStatus_t`，以与 cuBLAS 库中的其他类型保持一致。
- `cublasAlloc()` 和 `cublasFree()` 函数已弃用。此更改分别移除了 `cudaMalloc()` 和 `cudaFree()` 周围这些不必要的包装函数。
- 函数 `cublasSetKernelStream()` 已重命名为 `cublasSetStream()`，以与其他 CUDA 库保持一致。

旧版 cuBLAS API（在"使用 cuBLAS 旧版 API"中有更详细的说明）可通过包含头文件 `cublas.h` 来使用。由于旧版 API 与先前发布的 cuBLAS 库 API 完全相同，现有应用程序可以开箱即用，并自动使用此旧版 API，无需任何源代码更改。

当前 API 和旧版 cuBLAS API 不能在单个翻译单元中同时使用：同时包含 `cublas.h` 和 `cublas_v2.h` 头文件将导致编译错误，因为符号重新声明不兼容。

通常情况下，新应用程序不应使用旧版 cuBLAS API，现有应用程序如果需要复杂且优化的流并行性，或者如果从多个线程并发调用 cuBLAS 例程，则应转换为使用新 API。

在本文档的其余部分中，新的 cuBLAS Library API 将简称为 cuBLAS Library API。

如前所述，旧版 API 和 cuBLAS 库 API 的接口分别是头文件 `cublas.h` 和 `cublas_v2.h`。此外，使用 cuBLAS 库的应用需要链接到：

- Linux 上的 DSO `cublas.so`
- Windows 上的 DLL `cublas.dll`，或
- Mac OS X 上的动态库 `cublas.dylib`

> **Note**
>
> 注意
>
> 同一个动态库实现了新版和旧版 cuBLAS API。