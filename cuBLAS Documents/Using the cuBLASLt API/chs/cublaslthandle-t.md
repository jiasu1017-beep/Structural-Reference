### 3.3.3. cublasLtHandle_t

`cublasLtHandle_t` 类型是一个指向不透明结构的指针类型，该不透明结构保存了 cuBLASLt 库上下文。使用 `cublasLtCreate()` 初始化 cuBLASLt 库上下文并返回一个指向保存 cuBLASLt 库上下文的不透明结构的句柄，使用 `cublasLtDestroy()` 销毁先前创建的 cuBLASLt 库上下文描述符并释放相关资源。

> **注意**

注意
cuBLAS 句柄 (`cublasHandle_t`) 封装了一个 cuBLASLt 句柄。任何有效的 `cublasHandle_t` 都可以通过简单的类型转换来替代 `cublasLtHandle_t` 使用。但是，与 cuBLAS 句柄不同，cuBLASLt 句柄不与任何特定的 CUDA 上下文绑定，但与图形上下文绑定的 CUDA 上下文除外（从 CUDA 12.8 开始）。如果在当前 CUDA 上下文与图形上下文绑定时创建 cuBLASLt 句柄，则 cuBLASLt 会检测相应的共享内存限制并将其记录在句柄中。