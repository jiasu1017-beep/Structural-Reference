# 6.2 ConnectorOrientation 对象





ConnectorOrientation 对象用于为连接器分配连接器方向。

**访问**

```
import assembly
mdb.models[*name*].rootAssembly.connectorOrientations[*i*]
import odbAccess
session.odbs[*name*].rootAssembly.connectorOrientations[*i*]
```

### 6.2.1 ConnectorOrientation(...)

此方法创建一个 ConnectorOrientation 对象。

**路径**

```
mdb.models[*name*].rootAssembly.ConnectorOrientation
session.odbs[*name*].rootAssembly.ConnectorOrientation
```

**必需参数**

*region*

一个 [Set](pt01ch45pyo04.md) 对象，指定要分配方向的区域。

**可选参数**

*localCsys1*

一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定第一个连接器点的局部坐标系。此值可能为 None，表示全局坐标系。

*axis1*

一个 SymbolicConstant，指定基准坐标系的轴，在此轴上应用额外旋转。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle1*

一个 Float，指定额外旋转的角度。默认值为 0.0。

*orient2sameAs1*

一个 Boolean，指定第二个连接器点是否使用与第一个点相同的局部坐标系、轴和角度。默认值为 ON。

*localCsys2*

一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定第二个连接器点的局部坐标系。此值可能为 None，表示全局坐标系。

*axis2*

一个 SymbolicConstant，指定基准坐标系的轴，在此轴上应用额外旋转。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle2*

一个 Float，指定额外旋转的角度。默认值为 0.0。

**返回值**

一个 ConnectorOrientation 对象。

**异常**

无。

### 6.2.2 setValues(...)

此方法修改 ConnectorOrientation 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConnectorOrientation](pt01ch06pyo02.md#ker-connectororientation-connectororientation-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 6.2.3 成员

ConnectorOrientation 对象具有与 [ConnectorOrientation](pt01ch06pyo02.md#ker-connectororientation-connectororientation-pyc) 方法参数相同名称和描述的成员。




