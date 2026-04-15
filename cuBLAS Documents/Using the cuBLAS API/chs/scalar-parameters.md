### 2.1.5. 标量参数（Scalar Parameters）

使用标量参数的函数分为两类：

- **第一类**：通过主机或设备上的引用接收 alpha 和/或 beta 参数作为缩放因子的函数，例如 `gemm`。
- **第二类**：在主机或设备上返回标量结果的函数，例如 `amax()`、`amin()`、`asum()`、`rotg()`、`rotmg()`、`dot()` 和 `nrm2()`。

对于第一类函数，当指针模式设置为 `CUBLAS_POINTER_MODE_HOST` 时，标量参数 `alpha` 和/或 `beta` 可以分配在栈上或堆上，但不应放置在托管内存中。在底层，与这些函数相关的 CUDA 内核将使用 `alpha` 和/或 `beta` 的值启动。因此，如果它们分配在堆上，即使内核启动是异步的，也可以在调用返回后立即释放。当指针模式设置为 `CUBLAS_POINTER_MODE_DEVICE` 时，`alpha` 和/或 `beta` 必须在设备上可访问，并且在其值被修改之前内核必须已经完成。请注意，由于 `cudaFree()` 会隐式执行 `cudaDeviceSynchronize()`，因此在调用后仍然可以在 `alpha` 和/或 `beta` 上调用 `cudaFree()`，但这样做会违背使用此指针模式的初衷。

对于第二类函数，当指针模式设置为 `CUBLAS_POINTER_MODE_HOST` 时，这些函数会阻塞 CPU，直到 GPU 完成计算并将结果复制回主机。当指针模式设置为 `CUBLAS_POINTER_MODE_DEVICE` 时，这些函数会立即返回。在这种情况下，与矩阵和向量结果类似，标量结果只有在 GPU 上的例程执行完成后才可用。这需要适当的同步操作才能从主机读取结果。

无论哪种情况，指针模式 `CUBLAS_POINTER_MODE_DEVICE` 允许库函数完全异步执行，与主机无关，即使 `alpha` 和/或 `beta` 是由前一个内核生成的。例如，在使用 cuBLAS 库实现线性系统求解和特征值问题的迭代方法时，可能会出现这种情况。