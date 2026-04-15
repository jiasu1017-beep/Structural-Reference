### 3.4.30. cublasLtMatmulPreferenceCreate()

```c++

cublasStatus_t cublasLtMatmulPreferenceCreate(
      cublasLtMatmulPreference_t *pref);


```


此函数通过分配用于保存其不透明结构的内存来创建矩阵乘法启发式搜索偏好描述符。

**参数**:


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| pref |  | 输出 | 指向由此函数创建的矩阵乘法偏好描述符结构的指针。请参阅 cublasLtMatrixLayout_t。 |


**返回值**:


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |


请参阅 cublasStatus_t 获取有效返回码的完整列表。