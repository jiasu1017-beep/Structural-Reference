

### 3.4.45. cublasLtMatrixTransformDescDestroy()



```c++

cublasStatus_t cublasLtMatrixTransformDescDestroy(
      cublasLtMatrixTransformDesc_t transformDesc);


```


This function destroys a previously created matrix transform descriptor object.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| transformDesc |  | Input | Pointer to the structure holding the matrix transform descriptor that should be destroyed by this function. See cublasLtMatrixTransformDesc_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the operation was successful. |


See cublasStatus_t for a complete list of valid return codes.


