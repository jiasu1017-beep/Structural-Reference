# 61.4 BeamOrientation 对象





BeamOrientation 对象表示第一个梁截面轴 ![](../graphics/ker_eqn00406.gif) 的方向。不支持使用元素连通性列表中的附加节点来指定梁方向。

**访问**

```
odb.parts()[*name*].beamOrientations(*i*)
odb.rootAssembly().instances()[*name*].beamOrientations(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.beamOrientations(*i*)
```

### 61.4.1 成员

BeamOrientation 对象可以具有以下成员：

**原型**

```
odb_Set region() const;
odb_Enum::odb_OrientationMethodEnum method() const;
odb_SequenceFloat vector() const;
```

*method*

一个 odb_Enum::odb_OrientationMethodEnum，指定方向分配方法。可能的值为 odb_Enum::N1_COSINES、odb_Enum::CSYS 和 odb_Enum::VECT。

*region*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定定义梁方向的区域。

*vector*

一个 odb_SequenceFloat，指定梁截面 ![](../graphics/ker_eqn00406.gif) 方向的方向余弦。





