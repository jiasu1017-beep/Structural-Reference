# 7.3 Edge 对象





Edges 是一维几何区域。

**访问**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].edges[*i*]
mdb.models[*name*].parts[*name*].allInternalSurfaces[*name*].edges[*i*]
mdb.models[*name*].parts[*name*].allSets[*name*].edges[*i*]
mdb.models[*name*].parts[*name*].allSurfaces[*name*].edges[*i*]
mdb.models[*name*].parts[*name*].edges[*i*]
mdb.models[*name*].parts[*name*].sets[*name*].edges[*i*]
mdb.models[*name*].parts[*name*].surfaces[*name*].edges[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.edges[*i*]
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.allinstances.surfaces[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.allInternalSets[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.allInternalSurfaces[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.allSets[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.allSurfaces[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.edges[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].surfaces[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].edges[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].surfaces[*name*]\
.edges[*i*]
mdb.models[*name*].rootAssembly.sets[*name*].edges[*i*]
mdb.models[*name*].rootAssembly.surfaces[*name*].edges[*i*]
```

### 7.3.1 getCurvature(...)

此方法返回边缘上某个位置处的曲率信息。

**必需参数**

*parameter*

一个 Float，指定要计算曲率的边缘上的归一化参数位置。此参数与参数 *point* 互斥。

*point*

一个元组，表示要计算曲率的点的 *X*-、*Y*- 和 *Z*- 坐标。如果 *point* 不在边缘上，将尝试将其投影到边缘上并使用投影点。

**可选参数**

无。

**返回值**

一个字典，键为 'evaluationPoint'、'curvature'、'radius' 和 'tangent'，其中 'evaluationPoint' 指定计算曲率的位置；'curvature' 指定该位置处的曲率向量；'radius' 是曲率半径；'tangent' 指定该位置处边缘的切线。

**异常**

给定的边缘是直的。

### 7.3.2 getFaces()

此方法返回一个由共享此边缘的面 ID 组成的序列。

**参数**

无。

**返回值**

一个整数元组。

**异常**

无。

### 7.3.3 getAdjacentEdges()

此方法返回一个数组，包含共享此边缘至少一个顶点的边缘对象。

**参数**

无。

**返回值**

一个 [EdgeArray](pt01ch07pyo03.md) 对象，即 Edge 对象的序列。

**异常**

无。

### 7.3.4 getEdgesByEdgeAngle(...)

此方法返回一个边缘对象数组，通过递归查找相邻边缘获得，这些相邻边缘位于小于或等于指定面角的角度处。

**必需参数**

*angle*

一个 float，指定面角值（以度为单位）。

**可选参数**

无。

**返回值**

一个 [EdgeArray](pt01ch07pyo03.md) 对象，即 Edge 对象的序列。

**异常**

无。

### 7.3.5 getNodes()

此方法返回与边缘关联的节点对象数组。

**参数**

无。

**返回值**

一个 [MeshNodeArray](pt01ch31pyo09.md) 对象，即 [MeshNode](pt01ch31pyo09.md) 对象的序列。

**异常**

无。

### 7.3.6 getElements()

此方法返回与边缘关联的元素对象数组。

**参数**

无。

**返回值**

一个 [MeshElementArray](pt01ch31pyo05.md) 对象，即 [MeshElement](pt01ch31pyo05.md) 对象的序列。

**异常**

无。

### 7.3.7 getRadius()

此方法返回圆形边缘的半径。

**参数**

无。

**返回值**

一个 Float，指定半径。

**异常**

给定的边缘不是圆形的。

### 7.3.8 getSize(...)

此方法返回一个 Float，表示边缘的长度。

**必需参数**

无。

**可选参数**

*printResults*

一个 Bool，指定是否打印详细输出。默认值为 True。

**返回值**

一个 Float。

**异常**

无。

### 7.3.9 getVertices()

此方法返回包围此边缘的顶点索引序列。第一个索引指归一化曲线参数 = 0.0 的顶点，第二个索引指归一化曲线参数 = 1.0 的顶点。如果边缘是闭合曲线，则仅返回一个顶点索引。

**参数**

无。

**返回值**

一个整数元组。

**异常**

无。

### 7.3.10 成员

Edge 对象具有以下成员：

*index*

一个 Int，指定边缘在 EdgeArray 中的索引。

*isReferenceRep*

一个 Boolean，指定边缘是否属于零件或实例的参考表示。

*pointOn*

一个 Float 元组，指定位于边缘上的点的 *X*-、*Y*- 和 *Z*- 坐标。

*featureName*

一个 Float 元组，指定创建此边缘的特征名称。

*instanceName*

一个 Float 元组，指定此边缘的零件实例名称（如果适用）。




