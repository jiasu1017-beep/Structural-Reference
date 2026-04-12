# 61.2 AnalyticSurface 对象





AnalyticSurface 对象是一个可以用直线段和/或曲线段描述的几何表面。

**访问**

```
odb.parts()[*name*].analyticSurface()
odb.rootAssembly().instances()[*name*].analyticSurface()
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.analyticSurface()
```

### 61.2.1 成员

AnalyticSurface 对象具有以下成员：

**原型**

```
odb_String name() const;
odb_String type() const;
double filletRadius() const;
odb_SequenceSequenceFloat localCoordData() const;
odb_SequenceAnalyticSurfaceSegment segments() const;
```

*name*

一个 odb_String，指定解析表面的名称。

*type*

一个 odb_Enum::odb_typeEnum，指定 AnalyticSurface 对象的类型。可能的值为 odb_Enum::SEGMENTS、odb_Enum::CYLINDER 和 odb_Enum::REVOLUTION。

*filletRadius*

一个 Double，指定平滑相邻段之间不连续性的曲率半径。默认值为 0.0。

*segments*

一个 [OdbSequenceAnalyticSurfaceSegment](pt02ch61pyo23.md) 对象，指定与表面关联的轮廓。

*localCoordData*

一个 odb_SequenceSequenceFloat，如果使用的话，指定表示局部坐标系的点的全局坐标。





