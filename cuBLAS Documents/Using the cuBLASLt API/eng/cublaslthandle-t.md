

### 3.3.3. cublasLtHandle_t


The cublasLtHandle_t type is a pointer type to an opaque structure holding the cuBLASLt  library context. Use cublasLtCreate() to initialize the cuBLASLt library context and return a handle to an opaque structure holding the cuBLASLt library context, and use cublasLtDestroy() to destroy a previously created cuBLASLt library context descriptor and release the resources.


> **Note**

Note
cuBLAS handle (cublasHandle_t) encapsulates a cuBLASLt handle. Any valid cublasHandle_t can be used in place of cublasLtHandle_t with a simple cast. However, unlike a cuBLAS handle, a cuBLASLt handle is not tied to any particular CUDA context with the exception of CUDA contexts tied to a graphics context (starting from CUDA 12.8). If a cuBLASLt handle is created when the current CUDA context is tied to a graphics context, then cuBLASLt detects the corresponding shared memory limitations and records it in the handle.


