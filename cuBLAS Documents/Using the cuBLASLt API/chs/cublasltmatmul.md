

### 3.4.17. cublasLtMatmul()



```c++

cublasStatus_t cublasLtMatmul(
      cublasLtHandle_t               lightHandle,
      cublasLtMatmulDesc_t           computeDesc,
      const void                    *alpha,
      const void                    *A,
      cublasLtMatrixLayout_t         Adesc,
      const void                    *B,
      cublasLtMatrixLayout_t         Bdesc,
      const void                    *beta,
      const void                    *C,
      cublasLtMatrixLayout_t         Cdesc,
      void                          *D,
      cublasLtMatrixLayout_t         Ddesc,
      const cublasLtMatmulAlgo_t    *algo,
      void                          *workspace,
      size_t                         workspaceSizeInBytes,
      cudaStream_t                   stream);


```


This function computes the matrix multiplication of matrices A and B to produce the output matrix D, according to the following operation:


`D = alpha*(A*B) + beta*(C),`


where `A`, `B`, and `C` are input matrices, and `alpha` and `beta` are input scalars.


> **Note**

Note
This function supports both in-place matrix multiplication (C == D and Cdesc == Ddesc) and out-of-place matrix multiplication (C != D, both matrices must have the same data type, number of rows, number of columns, batch size, and memory order). In the out-of-place case, the leading dimension of C can be different from the leading dimension of D. Specifically the leading dimension of C can be 0 to achieve row or column broadcast. If Cdesc is omitted, this function assumes it to be equal to Ddesc.


The `workspace` pointer must be aligned to at least a multiple of 256 bytes.
The recommendations on `workspaceSizeInBytes` are the same as mentioned in the cublasSetWorkspace() section.


**Datatypes Supported:**


cublasLtMatmul() supports the following computeType, scaleType, Atype/Btype, and Ctype. Footnotes can be found at the end of this section.


| computeType | scaleType | Atype/Btype | Ctype | Bias Type 6 |
| --- | --- | --- | --- | --- |
| CUBLAS_COMPUTE_16F or
CUBLAS_COMPUTE_16F_PEDANTIC | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUBLAS_COMPUTE_32I or
CUBLAS_COMPUTE_32I_PEDANTIC | CUDA_R_32I | CUDA_R_8I | CUDA_R_32I | Epilogue is not supported. |
| CUDA_R_32F | CUDA_R_8I | CUDA_R_8I | Epilogue is not supported. |
| CUBLAS_COMPUTE_32F or
CUBLAS_COMPUTE_32F_PEDANTIC | CUDA_R_32F | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8I | CUDA_R_32F | Epilogue is not supported. |
| CUDA_R_16BF | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_R_16F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_C_32F 7 | CUDA_C_8I 7 | CUDA_C_32F 7 | Epilogue is not supported. |
| CUDA_C_32F 7 | CUDA_C_32F 7 |
| CUBLAS_COMPUTE_32F_FAST_16F or
CUBLAS_COMPUTE_32F_FAST_16BF or
CUBLAS_COMPUTE_32F_FAST_TF32 or
CUBLAS_COMPUTE_32F_EMULATED_16BFX9 | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_C_32F 7 | CUDA_C_32F 7 | CUDA_C_32F 7 | Epilogue is not supported. |
| CUBLAS_COMPUTE_64F or
CUBLAS_COMPUTE_64F_PEDANTIC or
CUBLAS_COMPUTE_64F_EMULATED_FIXEDPOINT | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F 6 |
| CUDA_C_64F 7 | CUDA_C_64F 7 | CUDA_C_64F 7 | Epilogue is not supported. |


To use IMMA kernels, one of the following sets of requirements, with the first being the preferred one, must be met:


1. Using a regular data ordering:

All matrix pointers must be 4-byte aligned. For even better performance, this condition should hold with 16 instead of 4.
Leading dimensions of matrices A, B, C must be multiples of 4.
Only the “TN” format is supported - A must be transposed and B non-transposed.
Pointer mode can be CUBLASLT_POINTER_MODE_HOST, CUBLASLT_POINTER_MODE_DEVICE or CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST. With the latter mode, the kernels support the CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE attribute.
Dimensions m and k must be multiples of 4.
2. Using the IMMA-specific data ordering on Ampere (compute capability 8.0) or Turing (compute capability 7.5) (but not Hopper, compute capability 9.0, or later) architecture - CUBLASLT_ORDER_COL32` for matrices A, C, D, and CUBLASLT_ORDER_COL4_4R2_8C (on Turing or Ampere architecture) or CUBLASLT_ORDER_COL32_2R_4R4 (on Ampere architecture) for matrix B:

Leading dimensions of matrices A, B, C must fulfill conditions specific to the memory ordering (see cublasLtOrder_t).
Matmul descriptor must specify CUBLAS_OP_T on matrix B and CUBLAS_OP_N (default) on matrix A and C.
If scaleType CUDA_R_32I is used, the only supported values for alpha and beta are 0 or 1.
Pointer mode can be CUBLASLT_POINTER_MODE_HOST, CUBLASLT_POINTER_MODE_DEVICE, CUBLASLT_POINTER_MODE_DEVICE_VECTOR or CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO. These kernels do not support CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE.
Only the “NT” format is supported - A must be non-transposed and B transposed.


| computeType | scaleType | Atype/Btype | Ctype | Bias Type |
| --- | --- | --- | --- | --- |
| CUBLAS_COMPUTE_32I or
CUBLAS_COMPUTE_32I_PEDANTIC | CUDA_R_32I | CUDA_R_8I | CUDA_R_32I | Non-default epilogue not supported. |
| CUDA_R_32F | CUDA_R_8I | CUDA_R_8I | CUDA_R_32F |


To use tensor- or block-scaled FP8 kernels, the following set of requirements must be satisfied:


- All matrix dimensions must meet the optimal requirements listed in Tensor Core Usage (i.e. pointers and matrix dimension must support 16-byte alignment).
- Scaling mode must meet the restrictions noted in the Scaling Mode Support Overview table.
- A must be transposed and B non-transposed (The “TN” format) on Ada (compute capability 8.9), Hopper (compute capability 9.0), and Blackwell GeForce (compute capability 12.x) GPUs.
- The compute type must be CUBLAS_COMPUTE_32F.
- The scale type must be CUDA_R_32F.


See the table below when using FP8 kernels:


| AType | BType | CType | DType | Bias Type |
| --- | --- | --- | --- | --- |
| CUDA_R_8F_E4M3 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |


To use block-scaled FP4 kernels, the following set of requirements must be satisfied:


- All matrix dimensions must meet the optimal requirements listed in Tensor Core Usage (i.e. pointers and matrix dimension must support 16-byte alignment).
- Scaling mode must be CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3
- A must be transposed and B non-transposed (The “TN” format)
- The compute type must be CUBLAS_COMPUTE_32F.
- The scale type must be CUDA_R_32F.


| AType | BType | CType | DType | Bias Type |
| --- | --- | --- | --- | --- |
| CUDA_R_4F_E2M1 | CUDA_R_4F_E2M1 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_4F_E2M1 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_4F_E2M1 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |


When A,B,C,D are planar-complex matrices (`CUBLASLT_MATRIX_LAYOUT_PLANE_OFFSET != 0`, see cublasLtMatrixLayoutAttribute_t) to make use of mixed precision tensor core acceleration, the following set of requirements must be satisfied:


| computeType | scaleType | Atype/Btype | Ctype |
| --- | --- | --- | --- |
| CUBLAS_COMPUTE_32F | CUDA_C_32F | CUDA_C_16F 7 | CUDA_C_16F 7 |
| CUDA_C_32F 7 |
| CUDA_C_16BF 7 | CUDA_C_16BF 7 |
| CUDA_C_32F 7 |


Experimental: To use cublasLtMatmul()  with grouped matrices, the following set of requirements must be satisfied:


- All matrix dimensions must meet the optimal requirements listed in Tensor Core Usage (i.e. pointers and matrix dimension must support 16-byte alignment).
- GPU with one of the following compute capabilities: 9.0, 10.x, 11.0.
- The batch mode of all matrices must be CUBLASLT_BATCH_MODE_GROUPED.
- The order type of all matrices must be CUBLASLT_ORDER_COL.
- The pointer mode must be CUBLASLT_POINTER_MODE_HOST or CUBLASLT_POINTER_MODE_DEVICE.
- The scale mode of matrices C  and D must be CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F.
- On GPUs with compute capability 9.0:



The scale mode of matrices A, B must be CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F, CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F, or CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F (for FP8 tensors)
The epilogue must be CUBLASLT_EPILOGUE_DEFAULT
The attributes CUBLASLT_MATMUL_DESC_ALPHA_BATCH_STRIDE and CUBLASLT_MATMUL_DESC_BETA_BATCH_STRIDE must be 0
- On GPUs with compute capability 10.x and 11.0:



The scale mode of matrices A, B must be CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F, CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0, CUBLASLT_MATMUL_MATRIX_SCALE_PER_BATCH_SCALAR_32F (for FP8 tensors), or CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3 (for FP4 tensors)
The epilogue must be CUBLASLT_EPILOGUE_DEFAULT or CUBLASLT_EPILOGUE_BIAS


| AType | BType | CType | DType | Bias Type |
| --- | --- | --- | --- | --- |
| CUDA_R_8F_E4M3 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |


> **Note**

Note
Because the shape information for the matrices is only available on the GPU (see CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_ARRAY, CUBLASLT_GROUPED_MATRIX_LAYOUT_COLS_ARRAY, and CUBLASLT_GROUPED_MATRIX_LAYOUT_LD_ARRAY), the arguments validation is very limited. So it is possible that invalid arguments are not detected which will result in an undefined behavior.


**NOTES:**


**6(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46)**
: Epilogue modes that combine ReLU, dReLu, GELU, or dGELU with Bias (see CUBLASLT_MATMUL_DESC_EPILOGUE in cublasLtMatmulDescAttributes_t) are not supported when D matrix memory order is defined as CUBLASLT_ORDER_ROW. For best performance when using the bias vector, specify zero beta and set pointer mode to CUBLASLT_POINTER_MODE_HOST.

**7(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17)**
: Use of CUBLAS_ORDER_ROW together with CUBLAS_OP_C (Hermitian operator) is not supported unless all of A, B, C, and D matrices use the CUBLAS_ORDER_ROW ordering.

**8(1,2,3,4,5,6,7,8,9,10)**
: FP8 DType is not supported when scaling modes are one of CUBLASLT_MATMUL_MATRIX_SCALE_OUTER_VEC_32F, CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F, and CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F.



**Parameters:**


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the allocated cuBLASLt handle for the cuBLASLt context. See cublasLtHandle_t. |
| computeDesc |  | Input | Handle to a previously created matrix multiplication descriptor of type cublasLtMatmulDesc_t. |
| alpha, beta | Device or host | Input | Pointers to the scalars used in the multiplication. |
| A, B, and C | Device | Input | Pointers to the GPU memory associated with the corresponding descriptors Adesc, Bdesc and Cdesc. |
| Adesc, Bdesc and Cdesc |  | Input | Handles to the previous created descriptors of the type cublasLtMatrixLayout_t. |
| D | Device | Output | Pointer to the GPU memory associated with the descriptor Ddesc. |
| Ddesc |  | Input | Handle to the previous created descriptor of the type cublasLtMatrixLayout_t. |
| algo |  | Input | Handle for matrix multiplication algorithm to be used. See cublasLtMatmulAlgo_t. When NULL, an implicit heuristics query with default search preferences will be performed to determine actual algorithm to use. |
| workspace | Device |  | Pointer to the workspace buffer allocated in the GPU memory. Must be 256B aligned (i.e. lowest 8 bits of address must be 0). |
| workspaceSizeInBytes |  | Input | Size of the workspace. |
| stream | Host | Input | The CUDA stream where all the GPU work will be submitted. |


**Returns:**


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_NOT_INITIALIZED | If cuBLASLt handle has not been initialized. |
| CUBLAS_STATUS_INVALID_VALUE | If the parameters are unexpectedly NULL, in conflict or in an impossible configuration. For example, when workspaceSizeInBytes is less than workspace required by the configured algo. |
| CUBLAS_STATUS_NOT_SUPPORTED | If the current implementation on the selected device doesn’t support the configured operation. |
| CUBLAS_STATUS_ARCH_MISMATCH | If the configured operation cannot be run using the selected device. |
| CUBLAS_STATUS_EXECUTION_FAILED | If CUDA reported an execution error from the device. |
| CUBLAS_STATUS_SUCCESS | If the operation completed successfully. |


See cublasStatus_t for a complete list of valid return codes.


