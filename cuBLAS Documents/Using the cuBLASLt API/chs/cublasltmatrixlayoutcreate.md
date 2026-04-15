### 3.4.35. cublasLtMatrixLayoutCreate()



```c++

cublasStatus_t cublasLtMatrixLayoutCreate( cublasLtMatrixLayout_t *matLayout,
                                           cudaDataType type,
                                           uint64_t rows,
                                           uint64_t cols,
                                           int64_t ld);


```


此函数通过分配保存其不透明结构所需的内存来创建矩阵布局描述符。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| matLayout |  | Output | 指向由此函数创建的矩阵布局描述符结构体的指针。请参见 cublasLtMatrixLayout_t。 |
| type |  | Input | 枚举类型，指定此函数创建的矩阵布局描述符的数据精度。请参见 cudaDataType_t。 |
| rows, cols |  | Input | 矩阵的行数和列数。 |
| ld |  | Input | 矩阵的主维度。在列优先布局中，这是跳转到下一列所需的元素个数。因此 ld >= m（行数）。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |


有关有效返回码的完整列表，请参见 cublasStatus_t。