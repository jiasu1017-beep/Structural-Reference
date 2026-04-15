### 2.1.9. 静态库支持

cuBLAS 库也可以以静态库的形式提供，在 Linux 上为 `libcublas_static.a`。静态 cuBLAS 库及其他所有静态数学库都依赖于一个名为 `libculibos.a` 的通用线程抽象层库。

例如，在 Linux 上，要使用动态库编译一个使用 cuBLAS 的小应用程序，可以使用以下命令：

```c++
nvcc myCublasApp.c  -lcublas  -o myCublasApp
```

而要使用静态 cuBLAS 库进行编译，则必须使用以下命令：

```c++
nvcc myCublasApp.c  -lcublas_static   -lculibos -o myCublasApp
```

也可以使用本机 Host C++ 编译器。根据 Host 操作系统的不同，链接时可能需要一些额外的库，如 `pthread` 或 `dl`。在 Linux 上建议使用以下命令：

```c++
g++ myCublasApp.c  -lcublas_static   -lculibos -lcudart_static -lpthread -ldl -I <cuda-toolkit-path>/include -L <cuda-toolkit-path>/lib64 -o myCublasApp
```

请注意，在后一种情况下，不需要 `cuda` 库。CUDA 运行时将在需要时显式尝试打开 `cuda` 库。对于没有安装 CUDA 驱动的系统，这允许应用程序优雅地处理此问题，并可能在有 CPU-only 路径可用时运行。

从 11.2 版本开始，使用类型化函数（typed functions）而不是扩展函数（`cublas**Ex()`）有助于在链接到静态 cuBLAS 库时减小二进制文件大小。