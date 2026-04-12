# 61.26 RebarOrientation 对象

RebarOrientation 对象表示钢筋参考的方向。

**访问**

```
odb.parts()[*name*].rebarOrientations(*i*)
odb.rootAssembly().instances()[*name*].rebarOrientations(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.rebarOrientations(*i*)
```

### 61.26.1 成员

RebarOrientation 对象可以具有以下成员：

**原型**

```
odb_Set region() const;
odb_DatumCsys csys() const;
odb_Enum::odb_AxisEnum axis() const;
float angle() const;
```

*axis*

一个 odb_Enum::odb_AxisEnum，指定圆柱形或球形基准坐标系的轴，关于该轴应用附加旋转。可能的值为 odb_Enum::AXIS_1、odb_Enum::AXIS_2 和 odb_Enum::AXIS_3。

*angle*

一个 Float，指定附加旋转的角度。

*region*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定定义钢筋方向区域。

*csys*

一个 [OdbDatumCsys](pt02ch61pyo14.md) 对象，指定基准坐标系。
