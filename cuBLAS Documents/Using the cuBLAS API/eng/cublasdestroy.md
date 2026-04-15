

### 2.4.2. cublasDestroy()



```c++

cublasStatus_t
cublasDestroy(cublasHandle_t handle)


```


This function releases hardware resources used by the cuBLAS library. This function is usually the last call with a particular handle to the cuBLAS library. Because cublasCreate() allocates some internal resources and the release of those resources by calling cublasDestroy() will implicitly call `cudaDeviceSynchronize()`, it is recommended to minimize the number of times these functions are called.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | the shut down succeeded |
| CUBLAS_STATUS_NOT_INITIALIZED | the library was not initialized |


