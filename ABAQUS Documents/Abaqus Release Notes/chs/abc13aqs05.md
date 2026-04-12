# 13.5 并行用户子程序





**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD

**优点：** 在所有并行模式中都支持并行用户子程序：线程并行和MPI并行。

**描述：** 已经建立了基础设施和程序更改以支持Abaqus用户子程序的并行执行。

对于线程，许多并行原语已在Fortran中公开，允许您用Fortran编写安全的多线程代码。这些原语也在C++中公开，尽管该语言有自己的编写多线程代码的设施。

对于MPI，已为Fortran和C++启用并提供了完整的本机支持。所有MPI调用都可以从Abaqus用户子程序内部调用。

已经做出特殊安排来为用户需求提供线程共享和线程本地存储。
**参考：**

**Abaqus分析用户指南**
- ["并行执行：概述，" 第3.5.1节](../usb/usb-link.md#usb-int-aparallelmodes)

**Abaqus用户子程序参考指南**
- ["可分配数组，" 第2.1.23节](../sub/sub-link.md#sub-utl-localarrays)




