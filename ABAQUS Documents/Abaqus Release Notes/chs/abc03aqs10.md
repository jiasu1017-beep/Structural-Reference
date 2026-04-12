# 3.10 将与孤立网格创建的几何面与网格关联





**产品：** Abaqus/CAE

**优势：** 当您从零件中的孤立网格单元面创建几何面时，Abaqus/CAE 默认现在会将新面与网格关联。

**描述：** 您可以使用 Geometry Edit 工具集从孤立网格元素的面创建几何体。默认情况下，新的几何面与网格关联；您可以选择更改此行为，如[图 3–1](abc03aqs10.md#rnb614-face-from-elem-face)所示。

**图 3–1** 从孤立单元面创建几何面的选项。

![](../graphics/rnb614-face-from-elem-face.png)

**Abaqus/CAE 使用：**
```
零件模块：
    ****Tools**![](../graphics/images/arrow.gif)**Geometry Edit****；**Face**：**From element faces**；**Options**：切换 **Associate face with mesh**
```

**参考：**

**Abaqus/CAE User's Guide**
- [“Create face from element faces，” Section 69.7.10](../usi/usi-link.md#usi-rep-help-repair-fromelem)




