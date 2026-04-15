### 2.1.12. CUDA Graphs 支持

cuBLAS 例程在大多数情况下可以不受限制地通过 CUDA Graph 流捕获进行捕获。

例外情况是那些将结果输出到主机缓冲区的例程（例如，当配置了指针模式 `CUBLAS_POINTER_MODE_HOST` 时的 `cublas<t>dot()`），因为这些例程会强制同步。

对于输入系数（如 `alpha`、`beta`），行为取决于指针模式的设置：

- 在 CUBLAS(LT)_POINTER_MODE_HOST 的情况下，系数值在图中被捕获。
- 在使用设备指针的指针模式下，系数值在图执行时通过设备指针访问。

> **注意**

当在 CUDA Graph 流捕获中捕获时，cuBLAS 例程可以通过流顺序分配 API（`cudaMallocAsync` 和 `cudaFreeAsync`）创建内存节点。但是，由于当前不支持子图或从设备启动的图中的内存节点，因此在此类场景中捕获 cuBLAS 例程可能会失败。为避免此问题，请使用 `cublasSetWorkspace()` 函数提供用户拥有的工作区内存。