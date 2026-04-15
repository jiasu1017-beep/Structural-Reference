

### 3.4.25. cublasLtMatmulDescCreate()



```c++

cublasStatus_t cublasLtMatmulDescCreate( cublasLtMatmulDesc_t *matmulDesc,
                                         cublasComputeType_t computeType,
                                         cudaDataType_t scaleType);


```


This function creates a matrix multiply descriptor by allocating the memory needed to hold its opaque structure.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matmulDesc |  | Output | Pointer to the structure holding the matrix multiply descriptor created by this function. See cublasLtMatmulDesc_t. |
| computeType |  | Input | Enumerant that specifies the data precision for the matrix multiply descriptor this function creates. See cublasComputeType_t. |
| scaleType |  | Input | Enumerant that specifies the data precision for the matrix transform descriptor this function creates. See cudaDataType_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See cublasStatus_t for a complete list of valid return codes.


