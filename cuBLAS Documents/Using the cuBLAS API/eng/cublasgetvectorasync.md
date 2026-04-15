

### 2.4.17. cublasGetVectorAsync()



```c++

cublasStatus_t
cublasGetVectorAsync(int n, int elemSize, const void *devicePtr, int incx,
                     void *hostPtr, int incy, cudaStream_t stream)


```


This function supports the 64-bit Integer Interface.


This function has the same functionality as cublasGetVector(), with the exception that the data transfer is done asynchronously (with respect to the host) using the given CUDA™ stream parameter.


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The operation completed successfully |
| CUBLAS_STATUS_INVALID_VALUE | The parameters incx, incy, or elemSize are not positive |
| CUBLAS_STATUS_MAPPING_ERROR | There was an error accessing GPU memory |


