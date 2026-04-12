# 34.22 OdbSequenceAnalyticSurfaceSegment 对象

描述解析曲面轮廓的 [AnalyticSurfaceSegment](pt01ch34pyo03.md) 序列。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].analyticSurface.segments
session.odbs[*name*].rootAssembly.instances[*name*].analyticSurface\
.segments
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.analyticSurface.segments
```

### 34.22.1 AnalyticSurfaceProfile()

此方法创建 OdbSequenceAnalyticSurfaceSegment 对象。

**路径**

```
odbAccess.AnalyticSurfaceProfile
```

**返回值**

OdbSequenceAnalyticSurfaceSegment 对象。

**异常**

无。

### 34.22.2 Start(...)

此方法添加描述曲面轮廓第一个段的 [AnalyticSurfaceSegment](pt01ch34pyo03.md)。

**必要参数**

*origin*

浮点数序列，指定起点坐标。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 34.22.3 Line(...)

此方法添加描述曲面轮廓线段的 [AnalyticSurfaceSegment](pt01ch34pyo03.md)。

**必要参数**

*endPoint*

浮点数序列，指定终点坐标。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 34.22.4 Circle(...)

此方法添加描述曲面轮廓圆弧段的 [AnalyticSurfaceSegment](pt01ch34pyo03.md)。

**必要参数**

*center*

浮点数序列，指定圆弧段的中心坐标。

*endPoint*

浮点数序列，指定圆弧段终点坐标。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 34.22.5 Parabola(...)

此方法添加描述曲面轮廓抛物线段的 [AnalyticSurfaceSegment](pt01ch34pyo03.md)。

**必要参数**

*middlePoint*

浮点数序列，指定抛物线段中点坐标。

*endPoint*

浮点数序列，指定抛物线段终点坐标。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 34.22.6 成员

OdbSequenceAnalyticSurfaceSegment 对象没有成员。
