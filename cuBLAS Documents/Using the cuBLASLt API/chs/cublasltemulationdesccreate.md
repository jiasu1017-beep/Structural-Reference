### 3.4.49. cublasLtEmulationDescCreate()



```c++

cublasStatus_t cublasLtEmulationDescCreate(cublasLtEmulationDesc_t* emulationDesc);


```


此函数用于创建新的仿真描述符。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| emulationDesc |  | Input | 指向先前创建的结构体的指针，该结构体保存由此函数查询的仿真描述符。请参阅 cublasLtEmulationDesc_t。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |


有关有效返回码的完整列表，请参阅 cublasStatus_t。