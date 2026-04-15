# 7. cuBLAS Fortran 绑定

cuBLAS 库使用基于 C 的 CUDA 工具链实现。因此，它提供了 C 风格的 API。这使得与用 C 和 C++ 编写的应用程序对接变得很简单，但该库也可以用于用 Fortran 编写的应用程序。特别是，cuBLAS 库使用从 1 开始的索引和 Fortran 风格的列优先存储来处理多维数据，以简化与 Fortran 应用程序的对接。不幸的是，Fortran 到 C 的调用约定未标准化，并且因平台和工具链而异。特别是，可能存在以下方面的差异：

- 符号名称（大写、名称修饰）
- 参数传递（按值或按引用）
- 字符串参数的传递（长度信息）
- 指针参数的传递（指针大小）
- 返回浮点或复合数据类型（例如单精度或复数数据类型）

为了在这些差异上提供最大的灵活性，cuBLAS Fortran 接口以包装函数的形式提供，并且是 Toolkit 交付的一部分。这些包装函数的 C 源代码位于 `src` 目录中，并以两种不同的形式提供：

- thunking 包装接口位于文件 fortran_thunking.c 中
- 直接包装接口位于文件 fortran.c 中

这两个文件之一的代码需要编译到应用程序中，以便调用 cuBLAS API 函数。提供源代码允许用户根据特定平台和工具链进行任何必要的更改。

这两个 C 文件中的代码已用于演示与 g77 3.2.3 和 g95 0.91（32 位 Linux）、g77 3.4.5 和 g95 0.91（64 位 Linux）、Intel Fortran 9.0 和 Intel Fortran 10.0（32 位和 64 位 Microsoft Windows XP）以及 g77 3.4.0 和 g95 0.92（Mac OS X）的互操作性。

请注意，对于 g77，需要使用编译器标志 `-fno-second-underscore` 才能使用这些包装器。此外，还应使用关于参数和返回值传递的默认调用约定。使用标志 -fno-f2c 会改变这两个方面的默认调用约定。

thunking 包装器允许与现有 Fortran 应用程序对接，而无需对应用程序进行任何更改。在每次调用期间，包装器分配 GPU 内存，将源数据从 CPU 内存空间复制到 GPU 内存空间，调用 cuBLAS，最后将结果复制回 CPU 内存空间并释放 GPU 内存。由于此过程会产生非常显著的调用开销，这些包装器旨在用于轻量级测试，而非生产代码。要使用 thunking 包装器，应用程序需要与文件 `fortran_thunking.c` 一起编译。

直接包装器（用于生产代码）用设备指针替换所有 BLAS 函数中的向量和矩阵参数。要使用这些接口，现有应用程序需要稍作修改，以在 GPU 内存空间中分配和释放数据结构（使用 `cuBLAS_ALLOC` 和 `cuBLAS_FREE`），并在 GPU 和 CPU 内存空间之间复制数据（使用 `cuBLAS_SET_VECTOR`、`cuBLAS_GET_VECTOR`、`cuBLAS_SET_MATRIX` 和 `cuBLAS_GET_MATRIX`）。`fortran.c` 中提供的示例包装器将设备指针映射到依赖于操作系统的类型 `size_t`，在 32 位平台上为 32 位宽，在 64 位平台上为 64 位宽。

在 Fortran 代码中处理设备指针上的索引运算的一种方法是使用 C 风格宏，并使用 C 预处理器进行展开，如下例所示。在 Linux 和 Mac OS X 上，一种预处理方法是使用 g77 编译器的选项 `-E -x f77-cpp-input`，或者使用 g95 或 gfortran 时只需使用选项 `-cpp`。在 Windows 平台上使用 Microsoft Visual C/C++，使用 'cl -EP' 可获得类似的结果。

```fortran

! 示例 B.1. 在主机上执行的 Fortran 77 应用程序
! ----------------------------------------------------------
    subroutine modify ( m, ldm, n, p, q, alpha, beta )
    implicit none
    integer ldm, n, p, q
    real*4 m (ldm, *) , alpha , beta
    external cublas_sscal
    call cublas_sscal (n-p+1, alpha , m(p,q), ldm)
    call cublas_sscal (ldm-p+1, beta, m(p,q), 1)
    return
    end

    program matrixmod
    implicit none
    integer M,N
    parameter (M=6, N=5)
    real*4 a(M,N)
    integer i, j
    external cublas_init
    external cublas_shutdown

    do j = 1, N
        do i = 1, M
            a(i, j) = (i-1)*M + j
        enddo
    enddo
    call cublas_init
    call modify ( a, M, N, 2, 3, 16.0, 12.0 )
    call cublas_shutdown
    do j = 1 , N
        do i = 1 , M
            write(*,"(F7.0$)") a(i,j)
        enddo
        write (*,*) ""
    enddo
    stop
    end


```

当传统的固定格式 Fortran 77 代码移植以使用 cuBLAS 库时，将 BLAS 调用替换为 cuBLAS 调用时，行长度通常会增加。较长的函数名称和可能的宏展开是影响因素。不小心超过最大行长度可能会导致难以发现的运行时错误，因此如果保留固定格式，应注意不要超过 72 列限制。

本章中的示例展示了一个在主机上用 Fortran 77 实现的小型应用程序，以及同一个应用程序在移植以使用 cuBLAS 库后使用非 thunking 包装器的版本。

第二个示例应在 64 位操作系统上编译，定义 ARCH_64 为 1；在 32 位操作系统上编译，定义 ARCH_64 为 0。例如，对于 g95 或 gfortran，可以直接在命令行上使用选项 `-cpp -DARCH_64=1` 来实现。

```fortran

! 示例 B.2. 使用非 thunking cuBLAS 调用的相同应用程序
!-------------------------------------------------------------
#define IDX2F(i,j,ld) ((((j)-1)*(ld))+((i)-1))
    subroutine modify ( devPtrM, ldm, n, p, q, alpha, beta )
    implicit none
    integer sizeof_real
    parameter (sizeof_real=4)
    integer ldm, n, p, q
#if ARCH_64
    integer*8 devPtrM
#else
    integer*4 devPtrM
#endif
    real*4 alpha, beta
    call cublas_sscal ( n-p+1, alpha,
    1                   devPtrM+IDX2F(p, q, ldm)*sizeof_real,
    2                   ldm)
    call cublas_sscal(ldm-p+1, beta,
    1                 devPtrM+IDX2F(p, q, ldm)*sizeof_real,
    2                 1)
    return
    end
    program matrixmod
    implicit none
    integer M,N,sizeof_real
#if ARCH_64
    integer*8 devPtrA
#else
    integer*4 devPtrA
#endif
    parameter(M=6,N=5,sizeof_real=4)
    real*4 a(M,N)
    integer i,j,stat
    external cublas_init, cublas_set_matrix, cublas_get_matrix
    external cublas_shutdown, cublas_alloc
    integer cublas_alloc, cublas_set_matrix, cublas_get_matrix
    do j=1,N
        do i=1,M
            a(i,j)=(i-1)*M+j
        enddo
    enddo
    call cublas_init
    stat= cublas_alloc(M*N, sizeof_real, devPtrA)
    if (stat.NE.0) then
        write(*,*) "device memory allocation failed"
        call cublas_shutdown
        stop
    endif
    stat = cublas_set_matrix(M,N,sizeof_real,a,M,devPtrA,M)
    if (stat.NE.0) then
        call cublas_free( devPtrA )
        write(*,*) "data download failed"
        call cublas_shutdown
        stop
    endif


```


—


*— 为格式化目的添加了空格。—*


—

```c++

call modify(devPtrA, M, N, 2, 3, 16.0, 12.0)
stat = cublas_get_matrix(M, N, sizeof_real, devPtrA, M, a, M )
if (stat.NE.0) then
call cublas_free ( devPtrA )
write(*,*) "data upload failed"
call cublas_shutdown
stop
endif
call cublas_free ( devPtrA )
call cublas_shutdown
do j = 1 , N
    do i = 1 , M
        write (*,"(F7.0$)") a(i,j)
    enddo
    write (*,*) ""
enddo
stop
end


```