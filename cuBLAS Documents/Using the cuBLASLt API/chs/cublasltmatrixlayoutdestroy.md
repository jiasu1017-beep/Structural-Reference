### 3.4.39. cublasLtMatrixLayoutDestroy()



```c++

cublasStatus_t cublasLtMatrixLayoutDestroy(
      cublasLtMatrixLayout_t matLayout);


```


此函数销毁先前创建的矩阵布局描述符对象。

**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| matLayout |  | Input | 指向矩阵布局描述符结构的指针，该结构由此函数销毁。请参阅 cublasLtMatrixLayout_t。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果操作成功。 |


有关有效返回码的完整列表，请参阅 cublasStatus_t。