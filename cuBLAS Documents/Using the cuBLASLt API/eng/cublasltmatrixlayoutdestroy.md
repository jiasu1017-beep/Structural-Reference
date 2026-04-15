

### 3.4.39. cublasLtMatrixLayoutDestroy()



```c++

cublasStatus_t cublasLtMatrixLayoutDestroy(
      cublasLtMatrixLayout_t matLayout);


```


This function destroys a previously created matrix layout descriptor object.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matLayout |  | Input | Pointer to the structure holding the matrix layout descriptor that should be destroyed by this function. See cublasLtMatrixLayout_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the operation was successful. |


See cublasStatus_t for a complete list of valid return codes.


