# 13.4 DisplayBody 对象

DisplayBody 对象定义了一种约束，使得指定的实例仅用于显示，不参与分析。然而，它在后处理过程中仍然可见，其在任何帧的位置由指定控制点的平移和旋转定义。

DisplayBody 对象派生自 [Constraint](pt01ch13pyo01.md) 对象。

**访问权限**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.4.1 DisplayBody(...)

此方法创建一个 DisplayBody 对象。

**路径**

```
mdb.models[*name*].DisplayBody
```

**必需参数**

*name*

字符串，指定约束存储库键。

*instance*

[PartInstance](pt01ch06pyo04.md) 对象，指定仅用于显示的部件实例。

*controlPoints*

[ModelDotArray](pt01ch07pyo12.md) 对象，指定 [PartInstance](pt01ch06pyo04.md) 的运动。控制点可以是 Vertex、ReferencePoint 或 MeshNode 对象。它们的运动将控制 PartInstance 的运动。如果此参数设置为空序列，则 PartInstance 在分析过程中将保持固定在空间中。该序列可以有一个对象或三个对象。

**可选参数**

无。

**返回值**

DisplayBody 对象。

**异常**

无。

### 13.4.2 setValues(...)

此方法修改 DisplayBody 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DisplayBody](pt01ch13pyo04.md#ker-displaybody-displaybody-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 13.4.3 成员

DisplayBody 对象的成员与 [DisplayBody](pt01ch13pyo04.md#ker-displaybody-displaybody-pyc) 方法的参数具有相同的名称和描述。

此外，DisplayBody 对象还有以下成员：

*suppressed*

布尔值，指定约束是否被抑制。默认值为 OFF。

### 13.4.4 对应的分析关键字

| [*DISPLAY BODY](../key/key-link.md#usb-kws-mdisplaybody) |
| --- |

