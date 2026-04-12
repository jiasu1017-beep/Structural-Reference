# 13.3 Coupling 对象

Coupling 对象定义了一组位于区域上的耦合节点与参考点之间的约束。

Coupling 对象派生自 [Constraint](pt01ch13pyo01.md) 对象。

**访问权限**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.3.1 Coupling(...)

此方法创建一个 Coupling 对象。

**路径**

```
mdb.models[*name*].Coupling
```

**必需参数**

*name*

字符串，指定约束存储库键。

*surface*

[Region](pt01ch45pyo03.md) 对象，指定耦合节点所在的曲面。

*controlPoint*

[Region](pt01ch45pyo03.md) 对象，指定约束控制点。

*influenceRadius*

符号常量 WHOLE_SURFACE 或浮点数，指定影响半径。

*couplingType*

符号常量，指定耦合约束类型。可能的值为 KINEMATIC、DISTRIBUTING 和 STRUCTURAL。

**可选参数**

*adjust*

布尔值，指定控制点是否将被调整（移动）到曲面。点将沿垂直于指定曲面的方向调整。默认值为 OFF。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定耦合自由度局部坐标系的初始方向。如果 *localCsys*=`None`，则在全局坐标系中定义耦合。默认值为 `None`。

*u1*

布尔值，指定对于运动学耦合约束，1 方向的位移分量是否约束到参考节点。默认值为 ON。

*u1* 参数仅在 *couplingType*=KINEMATIC 时适用。

*u2*

布尔值，指定对于运动学耦合约束，2 方向的位移分量是否约束到参考节点。默认值为 ON。

*u2* 参数仅在 *couplingType*=KINEMATIC 时适用。

*u3*

布尔值，指定对于运动学耦合约束，3 方向的位移分量是否约束到参考节点。默认值为 ON。

*u3* 参数仅在 *couplingType*=KINEMATIC 时适用。

*ur1*

布尔值，指定对于运动学耦合约束，绕 1 方向的旋转位移分量是否约束到参考节点。默认值为 ON。

*ur1* 参数仅在 *couplingType*=KINEMATIC 时适用。

*ur2*

布尔值，指定对于运动学耦合约束，绕 2 方向的旋转位移分量是否约束到参考节点。默认值为 ON。

*ur2* 参数仅在 *couplingType*=KINEMATIC 时适用。

*ur3*

布尔值，指定对于运动学耦合约束，绕 3 方向的旋转位移分量是否约束到参考节点。默认值为 ON。

*ur3* 参数仅在 *couplingType*=KINEMATIC 时适用。

*weightingMethod*

符号常量，指定用于计算分布权重因子的可选加权方法。可能的值为 UNIFORM、LINEAR、QUADRATIC 和 CUBIC。默认值为 UNIFORM。

*weightingMethod* 参数仅在 *couplingType*=DISTRIBUTING 时适用。

**返回值**

Coupling 对象。

**异常**

无。

### 13.3.2 setValues(...)

此方法修改 Coupling 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Coupling](pt01ch13pyo03.md#ker-coupling-coupling-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 13.3.3 成员

Coupling 对象的成员与 [Coupling](pt01ch13pyo03.md#ker-coupling-coupling-pyc) 方法的参数具有相同的名称和描述。

此外，Coupling 对象还有以下成员：

*suppressed*

布尔值，指定约束是否被抑制。默认值为 OFF。

### 13.3.4 对应的分析关键字

| [*COUPLING](../key/key-link.md#usb-kws-mcoupling) |
| --- |

