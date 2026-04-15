### 3.4.48. cublasLtEmulationDescInit()

```c++
cublasStatus_t cublasLtEmulationDescInit(cublasLtEmulationDesc_t emulationDesc);
```

此函数用于初始化一个先前分配的模拟描述符。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| emulationDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体保存由此函数查询的模拟描述符。参见 cublasLtEmulationDesc_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果预分配的空间大小不足。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |

有关有效的返回代码完整列表，请参见 cublasStatus_t。