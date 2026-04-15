# 8. 与其他库和工具的交互

本节描述了重要的需求和建议，以确保正确使用 cuBLAS 与其他库和工具。

## 8.1. nvprune

`nvprune` 支持对可重定位主机对象和静态库进行剪枝，使其仅包含针对特定目标架构的设备代码。在使用 cuBLAS 时，如果使用 `nvprune` 且计算能力的次版本号不同于 0，则需要特别小心。为减少二进制文件大小，cuBLAS 可能仅存储主要版本等效的 CUDA 二进制文件，以供不同次版本之间重复使用的内核。因此，为确保剪枝后的库不会因任意问题而失败，用户必须保留所选架构及其主要架构中所有先前次架构的二进制文件。

例如，以下调用将对 `libcublas_static.a` 进行剪枝，使其仅包含 sm_75（Turing）和 sm_70（Volta）cubin：

```c++

nvprune --generate-code code=sm_70 --generate-code code=sm_75 libcublasLt_static.a -o libcublasLt_static_sm70_sm75.a

```

应使用上述命令而非：

```c++

nvprune -arch=sm_75 libcublasLt_static.a -o libcublasLt_static_sm75.a

```