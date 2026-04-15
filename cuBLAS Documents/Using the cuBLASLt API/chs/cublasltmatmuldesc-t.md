### 3.3.8. cublasLtMatmulDesc_t

`cublasLtMatmulDesc_t` 是指向一个不透明结构的指针，该结构保存了矩阵乘法运算 `cublasLtMatmul()` 的描述信息。可以通过调用 `cublasLtMatmulDescCreate()` 创建描述符，并通过调用 `cublasLtMatmulDescDestroy()` 进行销毁。