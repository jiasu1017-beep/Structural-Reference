### 2.4.13. cublasGetVector()

```c++
cublasStatus_t
cublasGetVector(int n, int elemSize,
                const void *x, int incx, void *y, int incy)
```

此函数支持64位整数接口。

此函数将GPU内存空间中向量`x`的`n`个元素复制到主机内存空间中的向量`y`。两个向量中的元素都被假定为`elemSize`字节大小。源向量中连续元素之间的存储间距由`incx`给出，目标向量`y`的存储间距由`incy`给出。

由于假定二维矩阵采用列主序格式，如果向量是矩阵的一部分，则增量等于`1`会访问该矩阵的（部分）列。类似地，使用等于矩阵主维度的增量会访问该矩阵的（部分）行。

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 操作成功完成 |
| CUBLAS_STATUS_INVALID_VALUE | 参数incx、incy或elemSize不为正数 |
| CUBLAS_STATUS_MAPPING_ERROR | 访问GPU内存时出错 |