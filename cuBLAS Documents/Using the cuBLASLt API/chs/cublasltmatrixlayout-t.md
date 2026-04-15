### 3.3.18. cublasLtMatrixLayout_t

`cublasLtMatrixLayout_t` 是指向不透明结构的指针，该结构保存矩阵布局的描述信息。使用 `cublasLtMatrixLayoutCreate()` 或 `cublasLtGroupedMatrixLayoutCreate()` 创建描述符的实例，并使用 `cublasLtMatrixLayoutDestroy()` 销毁先前创建的描述符并释放资源。