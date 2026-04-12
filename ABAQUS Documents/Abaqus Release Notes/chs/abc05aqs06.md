# 5.6 DEM 分析的并行增强





**产品：** Abaqus/Explicit

**优势：** 由于 DEM 计算的域分解，离散单元法（DEM）模拟运行效率更高。

**说明：** 与 DEM 粒子接触相关的计算现在以域并行方式实现，从而在使用多个 CPU 时实现更好的并行扩展。与并行平滑粒子流体动力学（SPH）分析类似，使用动态域分解来避免 DEM 域之间的大空间重叠（因此保持良好的并行扩展），特别是在 DEM 粒子发生大相对运动之后。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["离散单元法，" 第 15.1.1 节](../usb/usb-link.md#usb-anl-ademanalysis)
