# 13.10 Tie 对象

Tie 对象定义两个曲面在模拟期间绑在一起。

Tie 对象派生自 [Constraint](pt01ch13pyo01.md) 对象。

**访问权限**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.10.1 Tie(...)

此方法创建一个 Tie 对象。

**路径**

```
mdb.models[*name*].Tie
```

**必需参数**

*name*

字符串，指定约束存储库键。

*master*

[Region](pt01ch45pyo03.md) 对象，指定主曲面的名称。

*slave*

[Region](pt01ch45pyo03.md) 对象，指定从曲面的名称。

**可选参数**

*adjust*

布尔值，指定是否调整绑定从节点的初始位置以位于主曲面上。默认值为 ON。

*positionToleranceMethod*

符号常量，指定用于确定位置容差的方法。可能的值为 COMPUTED 和 SPECIFIED。默认值为 COMPUTED。

*positionTolerance*

浮点数，指定位置容差。*positionTolerance* 参数仅在 *positionToleranceMethod*=SPECIFIED 时适用。默认值为 0.0。

*tieRotations*

布尔值，指定是否绑定旋转自由度。默认值为 ON。

*constraintRatioMethod*

符号常量，指定用于确定约束比例的方法。可能的值为 DEFAULT 和 SPECIFIED。默认值为 DEFAULT。

*constraintRatio*

浮点数，指定主参考曲面与平移约束应作用的从节点之间的分数距离。*constraintRatio* 参数仅在 *constraintRatioMethod*=SPECIFIED 时适用。默认值为 0.0。

*constraintEnforcement*

符号常量，指定离散化方法。可能的值为 SOLVER_DEFAULT、NODE_TO_SURFACE 和 SURFACE_TO_SURFACE。默认值为 SOLVER_DEFAULT。

*thickness*

布尔值，指定是否考虑壳单元厚度。默认值为 ON。

**返回值**

Tie 对象。

**异常**

无。

### 13.10.2 swapSurfaces()

此方法切换绑定约束的主曲面和从曲面。此命令仅在创建交互的步骤中有效。

**参数**

无。

**返回值**

无。

**异常**

无。

### 13.10.3 setValues(...)

此方法修改 Tie 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Tie](pt01ch13pyo10.md#ker-tie-tie-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 13.10.4 成员

Tie 对象的成员与 [Tie](pt01ch13pyo10.md#ker-tie-tie-pyc) 方法的参数具有相同的名称和描述。

此外，Tie 对象还有以下成员：

*suppressed*

布尔值，指定约束是否被抑制。默认值为 OFF。

### 13.10.5 对应的分析关键字

| [*TIE](../key/key-link.md#usb-kws-mtie) |
| --- |

