### 3.3.5. cublasLtMatmulAlgo_t

cublasLtMatmulAlgo_t 是一个不透明结构体，用于保存矩阵乘法算法的描述。该结构体可以被简单地序列化，并在后续使用相同版本的 cuBLAS 库时恢复使用，以节省再次选择正确配置的时间。