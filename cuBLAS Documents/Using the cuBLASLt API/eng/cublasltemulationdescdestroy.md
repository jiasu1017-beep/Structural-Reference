

### 3.4.50. cublasLtEmulationDescDestroy()



```c++

cublasStatus_t cublasLtEmulationDescDestroy(cublasLtEmulationDesc_t emulationDesc);


```


This function destroys a previously created emulation descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| emulationDesc |  | Input | Pointer to the previously created structure holding the emulation descriptor queried by this function. See cublasLtEmulationDesc_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the descriptor was destroyed successfully. |


See cublasStatus_t for a complete list of valid return codes.


