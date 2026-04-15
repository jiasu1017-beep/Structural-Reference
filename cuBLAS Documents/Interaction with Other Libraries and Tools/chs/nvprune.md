## 8.1. nvprune

`nvprune` 工具可对可重定位主机对象和静态库进行剪枝，使其仅包含特定目标架构的设备代码。对于 cuBLAS，如果使用 `nvprune` 处理次版本号不为 0 的计算能力，需要特别注意。为了减小二进制文件大小，cuBLAS 可能只为在不同次版本之间重用的内核存储 CUDA 二进制文件的主要版本等效文件。因此，为确保剪枝后的库不会在任意问题上失败，用户必须保留选定架构及其主要架构中所有先前次要架构的二进制文件。

例如，以下调用将 `libcublas_static.a` 剪枝为仅包含 sm_75（Turing）和 sm_70（Volta）cubins：

```c++
nvprune --generate-code code=sm_70 --generate-code code=sm_75 libcublasLt_static.a -o libcublasLt_static_sm70_sm75.a
```

此用法应替代以下方式：

```c++
nvprune -arch=sm_75 libcublasLt_static.a -o libcublasLt_static_sm75.a
```