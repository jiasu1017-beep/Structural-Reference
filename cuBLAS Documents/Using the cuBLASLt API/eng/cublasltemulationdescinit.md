

### 3.4.48. cublasLtEmulationDescInit()



```c++

cublasStatus_t cublasLtEmulationDescInit(cublasLtEmulationDesc_t emulationDesc);


```


This function initializes a previously allocated emulation descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| emulationDesc |  | Input | Pointer to the previously created structure holding the emulation descriptor queried by this function. See cublasLtEmulationDesc_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If the size of the pre-allocated space is insufficient. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See cublasStatus_t for a complete list of valid return codes.


