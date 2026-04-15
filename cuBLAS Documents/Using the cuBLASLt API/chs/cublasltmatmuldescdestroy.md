### 3.4.27. cublasLtMatmulDescDestroy()

```c++
cublasStatus_t cublasLtMatmulDescDestroy(
      cublasLtMatmulDesc_t matmulDesc);
```

此函数销毁先前创建的矩阵乘法描述符对象。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| matmulDesc |  | Input | 指向保存矩阵乘法描述符的结构的指针，该描述符应由此函数销毁。请参阅 cublasLtMatmulDesc_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果操作成功。 |

有关有效返回代码的完整列表，请参阅 cublasStatus_t。