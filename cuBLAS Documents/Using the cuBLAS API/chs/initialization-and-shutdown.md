## 6.2. 初始化和关闭（Initialization and Shutdown）

函数 `cublasInit()` 和 `cublasShutdown()` 用于初始化和关闭 cuBLAS 库。建议在任何其他函数调用之前先调用 `cublasInit()`。它会为当前绑定到调用它的主机线程的 GPU 设备分配硬件资源。

传统的初始化和关闭函数类似于 cuBLAS 库 API 例程 `cublasCreate()` 和 `cublasDestroy()`。