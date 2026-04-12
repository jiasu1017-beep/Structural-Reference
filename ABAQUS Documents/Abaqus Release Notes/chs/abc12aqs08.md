# 12.8 在 Abaqus/CAE 中请求参考汇温度和膜系数场输出







**产品：**Abaqus/CAE  

**优点：**您现在可以在 Abaqus/CAE 中请求参考汇温度和参考膜系数值，这提高了 Abaqus 产品功能的覆盖率。

**说明：**对于耦合热应力、耦合热电、耦合热电结构和传热过程，以下场输出变量现在在 Abaqus/CAE 中可用：
- SINKTEMP：参考汇温度
- FILMCOEF：参考膜系数值

**Abaqus/CAE 使用方法：**
```
Step 模块:
    Field output request editor: **Output Variables**: **Thermal**: **SINKTEMP** 和 **FILMCOEF**
```

**参考：**

**Abaqus/CAE User's Guide**
- ["Creating and modifying output requests," Section 14.4.5](../usi/usi-link.md#usi-sim-conc-varcomp)

