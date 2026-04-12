# 34.3 AnalyticSurfaceSegment 对象

解析曲面的单个段。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].analyticSurface.segments[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].analyticSurface\
.segments[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.analyticSurface.segments[*i*]
```

### 34.3.1 AnalyticSurfaceSegment(...)

此方法创建一个 AnalyticSurfaceSegment 对象。

**路径**

```
odbAccess.AnalyticSurfaceSegment
```

**必要参数**

*type*

一个 SymbolicConstant，指定 AnalyticSurfaceSegment 的类型。可能的值为 START、LINE、CIRCLE 和 PARABOLA。

*data*

浮点数序列的序列，指定表示 [AnalyticSurface](pt01ch34pyo02.md) 对象段的点的坐标。如果 *type*=CIRCLE，第一行包含端点坐标，第二行包含中心点坐标。如果 *type*=PARABOLA，第一行包含中点坐标，第二行包含端点坐标。如果 *type*=START 或 *type*=LINE，则单行包含起点/终点的坐标。

**可选参数**

无。

**返回值**

AnalyticSurfaceSegment 对象。

**异常**

无。

### 34.3.2 成员

AnalyticSurfaceSegment 对象的成员与 [AnalyticSurfaceSegment](pt01ch34pyo03.md#ker-analyticsurfacesegment-analyticsurfacesegment-pyc) 方法的参数具有相同的名称和描述。
