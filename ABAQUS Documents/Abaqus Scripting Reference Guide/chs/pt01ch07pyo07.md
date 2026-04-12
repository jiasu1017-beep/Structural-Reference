# 7.7 IgnoredEdge 对象





IgnoredEdge 对象是由虚拟拓扑特征抽象掉的一维几何区域。

**访问**

```
import part
mdb.models[*name*].parts[*name*].ignoredEdges[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.ignoredEdges[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].ignoredEdges[*i*]
```

### 7.7.1 getSize(...)

此方法返回一个 Float，表示边缘的长度。

**必需参数**

无。

**可选参数**

* printResults*

一个 Bool，指定是否打印详细输出。默认值为 True。

**返回值**

一个 Float。

**异常**

无。

### 7.7.2 getRadius()

此方法返回圆形 IgnoredEdge 的半径。

**参数**

无。

**返回值**

一个 Float，指定半径。

**异常**

给定的 IgnoredEdge 不是圆形的。

### 7.7.3 getCurvature(...)

此方法返回 IgnoredEdge 上的某个位置处的曲率信息。

**必需参数**

*parameter*

一个 Float，指定要计算曲率的 IgnoredEdge 上的归一化参数位置。此参数与参数 *point* 互斥。

*point*

一个元组，表示要计算曲率的点的 *X*-、*Y*- 和 *Z*- 坐标。如果 *point* 不在 IgnoredEdge 上，将尝试将其投影到 IgnoredEdge 上并使用投影点。

**可选参数**

无。

**返回值**

一个字典，键为 'evaluationPoint'、'curvature'、'radius'、'tangent'。其中 'evaluationPoint' 指定计算曲率的位置。'curvature' 指定该位置处的曲率向量。'radius' 是曲率半径，'tangent' 指定该位置处 IgnoredEdge 的切线。

**异常**

给定的 IgnoredEdge 是直的。

### 7.7.4 成员

IgnoredEdge 对象具有以下成员：

*index*

一个 Int，指定 IgnoredEdge 在 [IgnoredEdgeArray](pt01ch07pyo07.md) 中的索引。

*pointOn*

一个 Float 元组，指定位于边缘上的点的 *X*-、*Y*- 和 *Z*- 坐标。




