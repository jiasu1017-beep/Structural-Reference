### 4.2.1. cublasXtHandle_t

`cublasXtHandle_t` 类型是一个指向不透明结构的指针类型，用于保存 cuBLASXt API 上下文。必须使用 `cublasXtCreate()` 初始化 cuBLASXt API 上下文，且返回的句柄必须传递给所有后续的 cuBLASXt API 函数调用。上下文应在最后使用 `cublasXtDestroy()` 销毁。