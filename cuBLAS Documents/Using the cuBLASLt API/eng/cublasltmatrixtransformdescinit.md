

### 3.4.44. cublasLtMatrixTransformDescInit()



```c++

cublasStatus_t cublasLtMatrixTransformDescInit(
      cublasLtMatrixTransformDesc_t transformDesc,
      cudaDataType scaleType);


```


This function initializes a matrix transform descriptor in a previously allocated one.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| transformDesc |  | Output | Pointer to the structure holding the matrix transform descriptor initialized by this function. See cublasLtMatrixTransformDesc_t. |
| scaleType |  | Input | Enumerant that specifies the data precision for the matrix transform descriptor this function initializes. See cudaDataType_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See cublasStatus_t for a complete list of valid return codes.


