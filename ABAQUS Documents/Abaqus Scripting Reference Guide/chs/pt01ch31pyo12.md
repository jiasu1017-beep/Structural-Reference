# 31.13 MeshStats 对象

MeshStats 对象是用于保存网格统计信息的查询对象，由 `getMeshStats` 命令返回。此对象没有任何方法。

**访问**

```
import mesh
```

### 31.13.1 成员

MeshStats 对象具有以下成员：

*numPointElems*

一个整数，指定点元素的数量。

*numLineElems*

一个整数，指定线元素的数量。

*numQuadElems*

一个整数，指定四边形元素的数量。

*numTriElems*

一个整数，指定三角形元素的数量。

*numHexElems*

一个整数，指定六面体元素的数量。

*numWedgeElems*

一个整数，指定楔形元素的数量。

*numTetElems*

一个整数，指定四面体元素的数量。

*numPyramidElems*

一个整数，指定金字塔形元素的数量。

*numNodes*

一个整数，指定节点的数量。

*numMeshedRegions*

一个整数，指定包含网格的区域数量。
