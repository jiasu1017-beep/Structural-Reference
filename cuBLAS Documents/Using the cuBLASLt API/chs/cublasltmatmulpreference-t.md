### 3.3.12. cublasLtMatmulPreference_t

`cublasLtMatmulPreference_t` 是一个指向不透明结构体的指针，该结构体保存了 `cublasLtMatmulAlgoGetHeuristic()` 配置的偏好设置描述。使用 `cublasLtMatmulPreferenceCreate()` 创建描述符的一个实例，使用 `cublasLtMatmulPreferenceDestroy()` 销毁先前创建的描述符并释放资源。