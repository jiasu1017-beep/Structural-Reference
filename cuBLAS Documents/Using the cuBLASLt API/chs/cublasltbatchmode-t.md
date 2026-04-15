### 3.3.28. cublasLtBatchMode_t

| 值 | 描述 |
| --- | --- |
| CUBLASLT_BATCH_MODE_STRIDED | 批次中每个实例的矩阵以固定数量的元素偏移量位于前一实例的对应位置。 |
| CUBLASLT_BATCH_MODE_POINTER_ARRAY | 批次中每个实例的矩阵地址从设备指针数组中读取。 |
| CUBLASLT_BATCH_MODE_GROUPED | 实验性功能：每个组中实例的矩阵地址从设备指针数组中读取。每个组可以具有不同的列数、行数和前导维度。详见 cublasLtMatrixLayout_t。 |