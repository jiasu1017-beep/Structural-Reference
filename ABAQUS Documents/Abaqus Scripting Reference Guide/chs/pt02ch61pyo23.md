# 61.23 OdbSequenceAnalyticSurfaceSegment 对象

描述解析曲面轮廓的 [AnalyticSurfaceSegment](pt02ch61pyo03.md) 序列。

**访问**

```
odb.parts()[*name*].analyticSurface().segments()
odb.rootAssembly().instances()[*name*].analyticSurface().segments()
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.analyticSurface().segments()
```

### 61.23.1 Start(...)

此方法添加一个描述曲面轮廓第一段的 [AnalyticSurfaceSegment](pt02ch61pyo03.md)。

**原型**

```
void
Start(const odb_SequenceFloat& origin);
```

**必需参数**

*origin*

一个 odb_SequenceFloat，指定起点坐标。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 61.23.2 Line(...)

此方法添加一个描述曲面轮廓线段的 [AnalyticSurfaceSegment](pt02ch61pyo03.md)。

**原型**

```
void
Line(const odb_SequenceFloat& endPoint);
```

**必需参数**

*endPoint*

一个 odb_SequenceFloat，指定终点坐标。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 61.23.3 Circle(...)

此方法添加一个描述曲面轮廓圆弧段的 [AnalyticSurfaceSegment](pt02ch61pyo03.md)。

**原型**

```
void
Circle(const odb_SequenceFloat& center,
       const odb_SequenceFloat& endPoint);
```

**必需参数**

*center*

一个 odb_SequenceFloat，指定圆弧段的中心坐标。

*endPoint*

一个 odb_SequenceFloat，指定圆弧段的终点坐标。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 61.23.4 Parabola(...)

此方法添加一个描述曲面轮廓抛物线段的 [AnalyticSurfaceSegment](pt02ch61pyo03.md)。

**原型**

```
void
Parabola(const odb_SequenceFloat& middlePoint,
         const odb_SequenceFloat& endPoint);
```

**必需参数**

*middlePoint*

一个 odb_SequenceFloat，指定抛物线段的中间点坐标。

*endPoint*

一个 odb_SequenceFloat，指定抛物线段的终点坐标。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 61.23.5 成员

OdbSequenceAnalyticSurfaceSegment 对象没有成员。
