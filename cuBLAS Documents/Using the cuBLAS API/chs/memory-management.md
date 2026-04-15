## 6.4. 内存管理

旧版 cuBLAS 库 API 使用的内存分别使用 `cublasAlloc()` 和 `cublasFree()` 函数进行分配和释放。这些函数在 GPU 内存空间中创建和销毁一个对象，该对象能够容纳包含 `n` 个元素的数组，其中每个元素需要 `elemSize` 字节的存储空间。请参阅旧版 cuBLAS API 头文件"cublas.h"以获取这些函数的原型。

`cublasAlloc()` 函数是 `cudaMalloc()` 函数的包装器，因此 `cublasAlloc()` 返回的设备指针可以传递给任何 CUDA™ 设备内核函数。但是，这些设备指针不能在主机代码中被解引用。`cublasFree()` 函数是 `cudaFree()` 函数的包装器。