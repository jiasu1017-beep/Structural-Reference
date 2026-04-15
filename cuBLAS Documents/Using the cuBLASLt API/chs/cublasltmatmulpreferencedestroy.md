### 3.4.32. cublasLtMatmulPreferenceDestroy()



```c++

cublasStatus_t cublasLtMatmulPreferenceDestroy(
      cublasLtMatmulPreference_t pref);


```


此函数用于销毁先前创建的矩阵乘法偏好描述符对象。

**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| pref |  | 输入 | 指向保存矩阵乘法偏好描述符的结构体的指针，该描述符将由本函数销毁。请参阅 cublasLtMatmulPreference_t。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果操作成功。 |


有关完整的有效返回代码列表，请参阅 cublasStatus_t。