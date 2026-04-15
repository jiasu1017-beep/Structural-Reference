### 3.4.50. cublasLtEmulationDescDestroy()

```c++
cublasStatus_t cublasLtEmulationDescDestroy(cublasLtEmulationDesc_t emulationDesc);
```

此函数销毁先前创建的仿真描述符。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| emulationDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体持有由此函数查询的仿真描述符。参见 cublasLtEmulationDesc_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果描述符成功销毁。 |

有关有效返回码的完整列表，请参见 cublasStatus_t。