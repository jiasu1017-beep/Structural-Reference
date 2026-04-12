# 13.9 ShellSolidCoupling 对象

ShellSolidCoupling 对象定义两个曲面在模拟期间绑在一起。

ShellSolidCoupling 对象派生自 [Constraint](pt01ch13pyo01.md) 对象。

**访问权限**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.9.1 ShellSolidCoupling(...)

此方法创建一个 ShellSolidCoupling 对象。

**路径**

```
mdb.models[*name*].ShellSolidCoupling
```

**必需参数**

*name*

字符串，指定约束存储库键。

*shellEdge*

[Region](pt01ch45pyo03.md) 对象，指定壳边缘曲面的名称。

*solidFace*

[Region](pt01ch45pyo03.md) 对象，指定实体曲面的名称。

**可选参数**

*positionToleranceMethod*

符号常量，指定用于确定位置容差的方法。可能的值为 COMPUTED 和 SPECIFIED。默认值为 COMPUTED。

*positionTolerance*

浮点数，指定位置容差。默认值为 0.0。

*positionTolerance* 参数仅在 *positionToleranceMethod*=SPECIFIED 时适用。

**注意：** Abaqus 不会约束位于位置容差之外的实体面部区域上的节点。

*influenceDistanceMethod*

符号常量，指定用于确定影响距离的方法。可能的值为 DEFAULT 和 SPECIFIED。默认值为 DEFAULT。

*influenceDistance*

浮点数，指定影响距离。*influenceDistance* 参数仅在 *influenceDistanceMethod*=SPECIFIED 时适用。默认值为 0.0。

**返回值**

ShellSolidCoupling 对象。

**异常**

无。

### 13.9.2 setValues(...)

此方法修改 ShellSolidCoupling 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ShellSolidCoupling](pt01ch13pyo09.md#ker-shellsolidcoupling-shellsolidcoupling-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 13.9.3 成员

ShellSolidCoupling 对象的成员与 [ShellSolidCoupling](pt01ch13pyo09.md#ker-shellsolidcoupling-shellsolidcoupling-pyc) 方法的参数具有相同的名称和描述。

此外，ShellSolidCoupling 对象还有以下成员：

*suppressed*

布尔值，指定约束是否被抑制。默认值为 OFF。

### 13.9.4 对应的分析关键字

| [*SHELL TO SOLID COUPLING](../key/key-link.md#usb-kws-mshelltosolidcoupling) |
| --- |

