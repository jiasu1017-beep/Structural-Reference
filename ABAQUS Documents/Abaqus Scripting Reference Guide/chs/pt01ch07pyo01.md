# 7.1 Cell 对象





Cells 是几何体的体积区域。

**访问**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].cells[*i*]
mdb.models[*name*].parts[*name*].allSets[*name*].cells[*i*]
mdb.models[*name*].parts[*name*].cells[*i*]
mdb.models[*name*].parts[*name*].sets[*name*].cells[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.cells[*i*]
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.allInternalSets[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.allSets[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.sets[*name*].cells[*i*]
```

### 7.1.1 getSize(...)

此方法返回一个 Float，表示单元格体积。

**必需参数**

无。

**可选参数**

*printResults*

一个 Boolean，指定是否打印详细输出。默认值为 True。

**返回值**

一个 Float。

**异常**

无。

### 7.1.2 getFaces()

此方法返回一个由包围单元格的面 ID 组成的序列。

**参数**

无。

**返回值**

一个整数元组。

**异常**

无。

### 7.1.3 getEdges()

此方法返回一个由单元格上边缘 ID 组成的序列。

**参数**

无。

**返回值**

一个整数元组。

**异常**

无。

### 7.1.4 getVertices()

此方法返回一个由单元格上顶点 ID 组成的序列。

**参数**

无。

**返回值**

一个整数元组。

**异常**

无。

### 7.1.5 getAdjacentCells()

此方法返回一个共享单元格至少一个面的单元格对象数组。

**参数**

无。

**返回值**

一个 [CellArray](pt01ch07pyo01.md) 对象，即 Cell 对象的序列。

**异常**

无。

### 7.1.6 getNodes()

此方法返回与单元格关联的节点对象数组。

**参数**

无。

**返回值**

一个 [MeshNodeArray](pt01ch31pyo09.md) 对象，即 [MeshNode](pt01ch31pyo09.md) 对象的序列。

**异常**

无。

### 7.1.7 getElements()

此方法返回与单元格关联的元素对象数组。

**参数**

无。

**返回值**

一个 [MeshElementArray](pt01ch31pyo05.md) 对象，即 [MeshElement](pt01ch31pyo05.md) 对象的序列。

**异常**

无。

### 7.1.8 成员

Cell 对象具有以下成员：

*index*

一个 Int，指定单元格在 CellArray 中的索引。

*isReferenceRep*

一个 Boolean，指定单元格是否属于零件或实例的参考表示。

*pointOn*

一个 Float 元组，指定位于单元格上的点的 *X*-、*Y*- 和 *Z*- 坐标。

*featureName*

一个 Float 元组，指定创建此单元格的特征名称。

*instanceName*

一个 Float 元组，指定此单元格的零件实例名称（如果适用）。




