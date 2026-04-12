# 11.2 GPGPU 加速的直接方程求解器







**产品：**Abaqus/Standard  

**优点：**GPGPU 加速的直接方程求解器的性能得到了改进，GPGPU 内存需求已减少。

**说明：**对于解时间主要由直接方程求解器支配的大型模型，使用 GPGPU 可以显著减少分析的整体时间，如图 [图 11--1](abc11aqs02.md#rnb614-symm-solver-speedup) 所示。这些类型的模型主要使用实体单元，具有超过 100 万个方程。

**图 11-1** GPGPU 加速的直接求解器性能改进。

![](../graphics/rnb614-symm-solver-speedup.png)

**参考：**

**Abaqus Analysis User's Guide**
- ["Parallel execution in Abaqus/Standard," Section 3.5.2](../usb/usb-link.md#usb-int-astdparallel)

