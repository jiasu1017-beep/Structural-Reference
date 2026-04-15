

### 3.4.13. cublasLtLoggerOpenFile()



```c++

cublasStatus_t cublasLtLoggerOpenFile(const char* logFile);


```


Experimental: This function opens and sets the logging output file in the given path.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| logFile |  | Input | Path of the logging output file. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the logging file was successfully opened. |


See cublasStatus_t for a complete list of valid return codes.


