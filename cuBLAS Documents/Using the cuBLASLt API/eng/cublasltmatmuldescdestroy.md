

### 3.4.27. cublasLtMatmulDescDestroy()



```c++

cublasStatus_t cublasLtMatmulDescDestroy(
      cublasLtMatmulDesc_t matmulDesc);


```


This function destroys a previously created matrix multiply descriptor object.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matmulDesc |  | Input | Pointer to the structure holding the matrix multiply descriptor that should be destroyed by this function. See cublasLtMatmulDesc_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If operation was successful. |


See cublasStatus_t for a complete list of valid return codes.


