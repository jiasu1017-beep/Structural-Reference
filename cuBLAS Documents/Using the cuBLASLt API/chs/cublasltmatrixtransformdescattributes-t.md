### 3.3.22. cublasLtMatrixTransformDescAttributes_t

cublasLtMatrixTransformDescAttributes_t 是一个描述符结构，包含定义矩阵变换操作细节的属性。使用 cublasLtMatrixTransformDescGetAttribute() 和 cublasLtMatrixTransformDescSetAttribute() 来设置矩阵变换描述符的属性值。

| 值 | 描述 | 数据类型 |
| --- | --- | --- |
| CUBLASLT_MATRIX_TRANSFORM_DESC_SCALE_TYPE | 缩放类型。输入将转换为缩放类型以进行缩放和求和运算，然后结果将转换回输出类型以存储到内存中。支持的数据类型请参见 cudaDataType_t。 | int32_t |
| CUBLASLT_MATRIX_TRANSFORM_DESC_POINTER_MODE | 指定标量 alpha 和 beta 是通过引用传递的，无论在主机端还是设备端。默认值为：CUBLASLT_POINTER_MODE_HOST（即在主机端）。请参见 cublasLtPointerMode_t。 | int32_t |
| CUBLASLT_MATRIX_TRANSFORM_DESC_TRANSA | 指定对矩阵 A 执行的操作类型。默认值为：CUBLAS_OP_N（即非转置操作）。请参见 cublasOperation_t。 | int32_t |
| CUBLASLT_MATRIX_TRANSFORM_DESC_TRANSB | 指定对矩阵 B 执行的操作类型。默认值为：CUBLAS_OP_N（即非转置操作）。请参见 cublasOperation_t。 | int32_t |