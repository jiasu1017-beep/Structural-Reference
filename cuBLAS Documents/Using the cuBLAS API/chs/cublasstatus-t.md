### 2.2.2. cublasStatus_t

此类型用于函数状态返回值。所有 cuBLAS 库函数都会返回其状态，状态可以是以下值：

| 值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | cuBLAS 库未初始化。这通常是由于缺少先前的 `cublasCreate()` 调用、cuBLAS 例程调用的 CUDA Runtime API 错误或硬件设置错误造成的。 |
| | 纠正方法：在函数调用前调用 `cublasCreate()`；并检查硬件、适当版本的驱动程序和 cuBLAS 库是否正确安装。 |
| CUBLAS_STATUS_ALLOC_FAILED | cuBLAS 库内部的资源分配失败。这通常是由 `cudaMalloc()` 失败造成的。 |
| | 纠正方法：在函数调用之前，尽可能多地释放先前分配的内存。 |
| CUBLAS_STATUS_INVALID_VALUE | 向函数传递了不支持的值或参数（例如，负的向量大小）。 |
| | 纠正方法：确保传递的所有参数都具有有效值。 |
| CUBLAS_STATUS_ARCH_MISMATCH | 函数需要设备架构中不存在的功能；通常是由计算能力低于 5.0 造成的。 |
| | 纠正方法：在具有适当计算能力的设备上编译和运行应用程序。 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问 GPU 内存空间失败，这通常是由纹理绑定失败造成的。 |
| | 纠正方法：在函数调用之前，取消绑定任何先前绑定的纹理。 |
| CUBLAS_STATUS_EXECUTION_FAILED | GPU 程序执行失败。这通常是由 GPU 上内核启动失败造成的，可能由多种原因引起。 |
| | 纠正方法：检查硬件、适当版本的驱动程序和 cuBLAS 库是否正确安装。 |
| CUBLAS_STATUS_INTERNAL_ERROR | cuBLAS 内部操作失败。此错误通常是由 `cudaMemcpyAsync()` 失败造成的。 |
| | 纠正方法：检查硬件、适当版本的驱动程序和 cuBLAS 库是否正确安装。同时，检查传递给例程的内存是否在例程完成之前未被释放。 |
| CUBLAS_STATUS_NOT_SUPPORTED | 请求的功能不受支持。 |
| CUBLAS_STATUS_LICENSE_ERROR | 请求的功能需要许可证，在尝试检查当前许可时检测到错误。如果许可证不存在或已过期，或者环境变量 NVIDIA_LICENSE_FILE 设置不正确，则可能发生此错误。 |