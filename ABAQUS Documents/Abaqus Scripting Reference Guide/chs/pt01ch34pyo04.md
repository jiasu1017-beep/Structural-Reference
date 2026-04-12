# 34.2 AnalyticSurface 对象

AnalyticSurface 对象是可以用直线和/或曲线段描述的几何曲面。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].analyticSurface
session.odbs[*name*].rootAssembly.instances[*name*].analyticSurface
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.analyticSurface
```

### 34.2.1 成员

AnalyticSurface 对象具有以下成员：

*name*

一个字符串，指定解析曲面的名称。

*type*

一个 SymbolicConstant，指定 AnalyticSurface 对象的类型。可能的值为 SEGMENTS、CYLINDER 和 REVOLUTION。

*filletRadius*

一个 Float，指定平滑相邻段之间不连续性的曲率半径。默认值为 0.0。

*segments*

一个 [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md) 对象，指定与曲面关联的轮廓。

*localCoordData*

浮点数元组的元组，指定表示所使用的局部坐标系的点的全局坐标（如果使用）。
