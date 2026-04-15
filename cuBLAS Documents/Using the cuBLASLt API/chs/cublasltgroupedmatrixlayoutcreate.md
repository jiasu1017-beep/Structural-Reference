### 3.4.37. cublasLtGroupedMatrixLayoutCreate()

```c++
cublasStatus_t cublasLtGroupedMatrixLayoutCreate( cublasLtMatrixLayout_t *matLayout,
                                           cudaDataType type,
                                           int groupCount,
                                           const void* rows_array,
                                           const void* cols_array,
                                           const void* ld_array);
```

实验性：此函数通过分配存储其不透明结构所需的内存来创建分组矩阵布局描述符。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| matLayout |  | 输出 | 指向此函数创建的矩阵布局描述符结构的指针。参见 cublasLtMatrixLayout_t。 |
| type |  | 输入 | 指定此函数创建的矩阵布局描述符数据精度的枚举值。参见 cudaDataType_t。 |
| groupCount |  | 输入 | 分组矩阵布局描述符中的组数量。 |
| rows_array |  | 输入 | 指向分组矩阵布局描述符行数组的设备指针。 |
| cols_array |  | 输入 | 指向分组矩阵布局描述符列数组的设备指针。 |
| ld_array |  | 输入 | 指向分组矩阵布局描述符主维（leading dimension）数组的设备指针。 |

**返回**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |

有关有效返回码的完整列表，请参见 cublasStatus_t。