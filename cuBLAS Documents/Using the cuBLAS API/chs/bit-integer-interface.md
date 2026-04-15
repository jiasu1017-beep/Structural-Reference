### 2.1.13. 64位整数接口

cuBLAS 12版本引入了支持64位整数的函数。每个64位整数函数等效于32位整数函数，但有以下变化：

- 函数名添加`_64`后缀。
- 维度（问题大小）的数据类型从`int`更改为`int64_t`。维度的示例：`m`、`n`和`k`。
- 主维度的数据类型从`int`更改为`int64_t`。主维度的示例：`lda`、`ldb`和`ldc`。
- 向量增量的数据类型从`int`更改为`int64_t`。向量增量的示例：`incx`和`incy`。

例如，考虑以下32位整数函数：

```c++

cublasStatus_t cublasSetMatrix(int rows, int cols, int elemSize, const void *A, int lda, void *B, int ldb);
cublasStatus_t cublasIsamax(cublasHandle_t handle, int n, const float *x, int incx, int *result);
cublasStatus_t cublasSsyr(cublasHandle_t handle, cublasFillMode_t uplo, int n, const float *alpha, const float *x, int incx, float *A, int lda);


```

等效的64位整数函数为：

```c++

cublasStatus_t cublasSetMatrix_64(int64_t rows, int64_t cols, int64_t elemSize, const void *A, int64_t lda, void *B, int64_t ldb);
cublasStatus_t cublasIsamax_64(cublasHandle_t handle, int64_t n, const float *x, int64_t incx, int64_t *result);
cublasStatus_t cublasSsyr_64(cublasHandle_t handle, cublasFillMode_t uplo, int64_t n, const float *alpha, const float *x, int64_t incx, float *A, int64_t lda);


```

并非每个函数都有64位整数等效版本。例如，`cublasSetMathMode()`没有任何可以有意义地使用`int64_t`的参数。为简洁起见，本文档不再单独列出64位整数API，仅说明相关函数存在64位整数版本。