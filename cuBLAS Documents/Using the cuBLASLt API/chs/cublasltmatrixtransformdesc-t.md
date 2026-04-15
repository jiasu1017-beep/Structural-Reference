### 3.3.21. cublasLtMatrixTransformDesc_t¶

`cublasLtMatrixTransformDesc_t` 是一个指向不透明结构体的指针，该结构体保存矩阵变换操作的描述信息。使用 `cublasLtMatrixTransformDescCreate()` 创建描述符的一个实例，并使用 `cublasLtMatrixTransformDescDestroy()` 销毁先前创建的描述符以及释放相关资源。