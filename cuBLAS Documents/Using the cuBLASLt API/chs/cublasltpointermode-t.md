### 3.3.24. cublasLtPointerMode_t

cublasLtPointerMode_t 是一个枚举类型，用于设置缩放因子 `alpha` 和 `beta` 的指针模式。

| 值 | 描述 |
| --- | --- |
| CUBLASLT_POINTER_MODE_HOST = CUBLAS_POINTER_MODE_HOST | 与 CUBLAS_POINTER_MODE_HOST 匹配，指针指向主机内存中的单个值。 |
| CUBLASLT_POINTER_MODE_DEVICE = CUBLAS_POINTER_MODE_DEVICE | 与 CUBLAS_POINTER_MODE_DEVICE 匹配，指针指向设备内存中的单个值。 |
| CUBLASLT_POINTER_MODE_DEVICE_VECTOR = 2 | 指针指向设备内存向量，长度等于矩阵 D 的行数。 |
| CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO = 3 | alpha 指针指向设备内存向量，长度等于矩阵 D 的行数，beta 为零。 |
| CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST = 4 | alpha 指针指向设备内存向量，长度等于矩阵 D 的行数，beta 为主机内存中的单个值。 |


> **注意**

注意
当任何矩阵的 cublasLtBatchMode_t 设置为 CUBLASLT_BATCH_MODE_POINTER_ARRAY 或 CUBLASLT_BATCH_MODE_GROUPED 时，仅支持 CUBLASLT_POINTER_MODE_HOST 和 CUBLASLT_POINTER_MODE_DEVICE 这两种指针模式。