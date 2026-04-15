## 8.1. nvprune

`nvprune` 支持剪裁可重定位主机对象和静态库，使其仅包含针对特定目标架构的设备代码。对于 cuBLAS，如果使用 `nvprune` 处理次版本号不为 0 的计算能力，则需要特别小心。为了减小二进制大小，cuBLAS 可能只为在不同次版本之间重复使用的内核存储 CUDA 二进制文件的主要版本等效版本。因此，为了确保剪裁后的库在处理任意问题时不会出现问题，用户必须在所选架构及其主要架构的所有先前次版本架构中保留二进制文件。

例如，以下调用会将 `libcublasLt_static.a` 剪裁为仅包含 sm_75（Turing）和 sm_70（Volta）cubins：

```c++

nvprune --generate-code code=sm_70 --generate-code code=sm_75 libcublasLt_static.a -o libcublasLt_static_sm70_sm75.a

```

上述命令应替代以下写法：

```c++

nvprune -arch=sm_75 libcublasLt_static.a -o libcublasLt_static_sm75.a

```