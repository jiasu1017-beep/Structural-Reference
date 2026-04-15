

### 3.4.14. cublasLtLoggerSetLevel()



```c++

cublasStatus_t cublasLtLoggerSetLevel(int level);


```


Experimental: This function sets the value of the logging level.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| level |  | Input | Value of the logging level. See cuBLASLt Logging. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If the value was not a valid logging level. See cuBLASLt Logging. |
| CUBLAS_STATUS_SUCCESS | If the logging level was successfully set. |


See cublasStatus_t for a complete list of valid return codes.


