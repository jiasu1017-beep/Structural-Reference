# 25.43 GeometricProperties 对象

GeometricProperties 对象指定表面交互属性。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].geometricProperties
```

### 25.43.1 GeometricProperties(...)

此方法创建一个 GeometricProperties 对象。

**路径**

```
mdb.models[*name*].interactionProperties[*name*].GeometricProperties
```

**必需参数**

无。

**可选参数**

*contactArea*

浮点数，指定二维模型的表面平面外厚度或基于节点的表面上每个节点的横截面积。默认值为 1.0。

*padThickness*

 `None` 或浮点数，指定接触表面之间界面层的厚度。如果 *padThickness*=`None`，则没有界面层。默认值为 `None`。

**返回值**

GeometricProperties 对象。

**异常**

无。

### 25.43.2 setValues(...)

此方法修改 GeometricProperties 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [GeometricProperties](pt01ch25pyo43.md#ker-geometricproperties-geometricproperties-pyc) 方法的参数相同。

**返回值**

无。

**异常**

无。

### 25.43.3 成员

GeometricProperties 对象的成员与 [GeometricProperties](pt01ch25pyo43.md#ker-geometricproperties-geometricproperties-pyc) 方法的参数具有相同的名称和描述。

### 25.43.4 对应的分析关键字

| [*SURFACE INTERACTION](../key/key-link.md#usb-kws-hsurfaceinteraction) |
| --- |



