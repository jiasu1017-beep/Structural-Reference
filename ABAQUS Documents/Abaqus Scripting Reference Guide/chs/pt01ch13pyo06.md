# 13.7 MultipointConstraint 对象

MultipointConstraint 对象定义了一组位于区域上的多点约束节点与参考点之间的约束。

MultipointConstraint 对象派生自 [Constraint](pt01ch13pyo01.md) 对象。

**访问权限**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.7.1 MultipointConstraint(...)

此方法创建一个 MultipointConstraint 对象。

**路径**

```
mdb.models[*name*].MultipointConstraint
```

**必需参数**

*name*

字符串，指定约束存储库键。

*surface*

[Region](pt01ch45pyo03.md) 对象，指定 MultipointConstraint 节点所在的曲面。

*controlPoint*

[Region](pt01ch45pyo03.md) 对象，指定约束控制点。

*mpcType*

符号常量，指定约束的 MPC 类型。可能的值为 BEAM_MPC、ELBOW_MPC、PIN_MPC、LINK_MPC、TIE_MPC 和 USER_MPC。

**可选参数**

*csys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定 MultipointConstraint 自由度局部坐标系的初始方向。如果 *localCsys*=`None`，则在全局坐标系中定义 MultipointConstraint。默认值为 `None`。

*userType*

整数，指定用于在用户定义的 MultipointConstraint 中区分不同约束类型的值。默认值为 0。

*userType* 参数仅在 *mpcType*=USER_MPC 时适用。

*userMode*

符号常量，指定用户定义约束的模式。可能的值为 DOF_MODE_MPC 和 NODE_MODE_MPC。默认值为 DOF_MODE_MPC。

*userMode* 参数仅在 *mpcType*=USER_MPC 时适用。

**返回值**

MultipointConstraint 对象。

**异常**

无。

### 13.7.2 setValues(...)

此方法修改 MultipointConstraint 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [MultipointConstraint](pt01ch13pyo07.md#ker-multipointconstraint-multipointconstraint-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 13.7.3 成员

MultipointConstraint 对象的成员与 [MultipointConstraint](pt01ch13pyo07.md#ker-multipointconstraint-multipointconstraint-pyc) 方法的参数具有相同的名称和描述。

此外，MultipointConstraint 对象还有以下成员：

*suppressed*

布尔值，指定约束是否被抑制。默认值为 OFF。

### 13.7.4 对应的分析关键字

| [*MPC](../key/key-link.md#usb-kws-mmpc) |
| --- |

