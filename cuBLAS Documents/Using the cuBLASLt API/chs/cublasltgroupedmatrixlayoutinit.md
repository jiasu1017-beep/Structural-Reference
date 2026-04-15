### 3.4.38. cublasLtGroupedMatrixLayoutInit()

```c++

cublasStatus_t cublasLtGroupedMatrixLayoutInit( cublasLtMatrixLayout_t matLayout,
                                         cudaDataType type,
                                         int groupCount,
                                         const void* rows_array,
                                         const void* cols_array,
                                         const void* ld_array);


```

实验性：此函数初始化先前已分配的分组合矩阵布局描述符。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| matLayout |  | 输出 | 指向由此函数初始化的矩阵布局描述符结构体的指针。请参阅 cublasLtMatrixLayout_t。 |
| type |  | 输入 | 指定此函数初始化的矩阵布局描述符数据精度的枚举值。请参阅 cudaDataType_t。 |
| groupCount |  | 输入 | 分组合矩阵布局描述符中的组数。 |
| rows_array |  | 输入 | 指向分组合矩阵布局描述符行数组的设备指针。 |
| cols_array |  | 输入 | 指向分组合矩阵布局描述符列数组的设备指针。 |
| ld_array |  | 输入 | 指向分组合矩阵布局描述符主维数组的设备指针。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |

请参阅 cublasStatus_t 以获取有效返回代码的完整列表。