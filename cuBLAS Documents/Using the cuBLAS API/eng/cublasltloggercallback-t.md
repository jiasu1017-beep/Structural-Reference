

### 3.3.4. cublasLtLoggerCallback_t


cublasLtLoggerCallback_t is a callback function pointer type. A callback function can be set using cublasLtLoggerSetCallback().


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| logLevel |  | Output | See cuBLASLt Logging. |
| functionName |  | Output | The name of the API that logged this message. |
| message |  | Output | The log message. |


