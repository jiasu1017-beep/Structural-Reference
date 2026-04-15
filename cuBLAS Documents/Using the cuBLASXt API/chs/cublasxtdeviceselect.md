### 4.3.3. cublasXtDeviceSelect()

```c++
cublasXtDeviceSelect(cublasXtHandle_t handle, int nbDevices, int deviceId[])
```

此函数允许用户提供将参与后续cuBLASXt API数学函数调用的GPU设备数量及其各自的ID。此函数将为列表中的每个GPU创建一个cuBLAS上下文。目前，设备配置是静态的，在数学函数调用之间无法更改。因此，此函数应在`cublasXtCreate`之后仅调用一次。要运行多个配置，应创建多个cuBLASXt API上下文。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 用户调用成功 |
| CUBLAS_STATUS_INVALID_VALUE | 无法访问至少一个设备，或者无法在至少一个设备上创建cuBLAS上下文 |
| CUBLAS_STATUS_ALLOC_FAILED | 无法分配某些资源 |