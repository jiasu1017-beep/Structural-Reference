# 61.3 AnalyticSurfaceSegment 对象





解析表面的单个段。

**访问**

```
odb.parts()[*name*].analyticSurface().segments(*i*)
odb.rootAssembly().instances()[*name*].analyticSurface().segments(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.analyticSurface().segments(*i*)
```

### 61.3.1 成员

AnalyticSurfaceSegment 对象具有以下成员：

**原型**

```
odb_String type() const;
odb_SequenceSequenceFloat data() const;
```

*type*

一个 odb_Enum::odb_typeEnum，指定 AnalyticSurfaceSegment 的类型。可能的值为 odb_Enum::START、odb_Enum::LINE、odb_Enum::CIRCLE 和 odb_Enum::PARABOLA。

*data*

一个 odb_SequenceSequenceFloat，指定表示 [AnalyticSurface](pt02ch61pyo02.md) 对象段的点坐标。如果 *type*=odb_Enum::CIRCLE，第一行包含端点坐标，第二行包含中心点坐标。如果 *type*=odb_Enum::PARABOLA，第一行包含中点坐标，第二行包含端点坐标。如果 *type*=odb_Enum::START 或 *type*=odb_Enum::LINE，单行包含起点/终点的坐标。





