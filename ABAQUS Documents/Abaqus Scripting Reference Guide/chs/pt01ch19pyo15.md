# 19.15 TwoPointSpringDashpot 对象









TwoPointSpringDashpot 对象定义部件或装配上两点之间的弹簧和/或阻尼器。

TwoPointSpringDashpot 对象派生自 [SpringDashpot](pt01ch19pyo13.md) 对象。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.springDashpots[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.springDashpots[*name*]
```

### 19.15.1 TwoPointSpringDashpot(...)

此方法创建 TwoPointSpringDashpot 对象。

**路径**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.TwoPointSpringDashpot
mdb.models[*name*].rootAssembly.engineeringFeatures\
.TwoPointSpringDashpot
```

**必需参数**

*name*

一个 String，指定存储库键。

*regionPairs*

一个 [Region](pt01ch45pyo03.md) 对象对的序列，指定应用弹簧和/或阻尼器之间的点。

*axis*

一个 SymbolicConstant，指定弹簧和/或阻尼器的轴是跟随节点旋转还是在指定方向。可能的值为 NODAL_LINE 和 FIXED_DOF。

**可选参数**

*dof1*

一个 Int，指定弹簧和/或阻尼器在其第一点处关联的 degrees of freedom。*dof1* 参数仅在 *axis*=FIXED_DOFS 时适用。默认值为 0。

*dof2*

一个 Int，指定弹簧和/或阻尼器在其第二点处关联的 degrees of freedom。*dof2* 参数仅在 *axis*=FIXED_DOFS 时适用。默认值为 0。

*orientation*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定弹簧和/或阻尼器的局部方向。如果 *orientation*=`None`，则弹簧和/或阻尼器数据在全局坐标系中定义。默认值为 `None`。

*orientation* 参数仅在 *axis*=FIXED_DOFS 时适用。

*springBehavior*

一个 Boolean，指定是否将弹簧行为应用于所选点对。默认值为 OFF。

必须指定 *springBehavior*=ON 或 *dashpotBehavior*=ON 中的至少一个。

*dashpotBehavior*

一个 Boolean，指定是否将阻尼器行为应用于所选点对。默认值为 OFF。

必须指定 *springBehavior*=ON 或 *dashpotBehavior*=ON 中的至少一个。

*springStiffness*

一个 Float，指定弹簧的相对位移力。默认值为 0.0。

*dashpotCoefficient*

一个 Float，指定阻尼器的相对速度力。默认值为 0.0。

**返回值**

一个 TwoPointSpringDashpot 对象。

**异常**

无。

### 19.15.2 setValues(...)

此方法修改 TwoPointSpringDashpot 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [TwoPointSpringDashpot](pt01ch19pyo15.md#ker-twopointspringdashpot-twopointspringdashpot-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 19.15.3 成员

TwoPointSpringDashpot 对象具有与 [TwoPointSpringDashpot](pt01ch19pyo15.md#ker-twopointspringdashpot-twopointspringdashpot-pyc) 方法的参数相同的名称和描述的成员。

此外，TwoPointSpringDashpot 对象还有以下成员：

*suppressed*

一个 Boolean，指定弹簧/阻尼器是否被抑制。默认值为 OFF。

### 19.15.4 对应的分析关键字

| [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=SPRINGA; [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=SPRING2; [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=DASHPOTA; [*ELEMENT](../key/key-link.md#usb-kws-melement), TYPE=DASHPOT2; [*SPRING](../key/key-link.md#usb-kws-mspring); [*DASHPOT](../key/key-link.md#usb-kws-mdashpot) |
| --- |





