### 2.2.1. cublasHandle_t

`cublasHandle_t` 类型是一个指向不透明结构的指针类型，用于保存 cuBLAS 库上下文。cuBLAS 库上下文必须使用 `cublasCreate()` 进行初始化，并且返回的句柄必须传递给所有后续的库函数调用。上下文应在最后使用 `cublasDestroy()` 进行销毁。