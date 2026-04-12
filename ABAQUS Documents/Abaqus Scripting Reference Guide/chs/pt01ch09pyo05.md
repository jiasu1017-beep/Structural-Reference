# 9.5 AccelerationBCState 对象

AccelerationBCState 对象存储加速度边界条件在步骤中的传播数据。系统为每个步骤由 [AccelerationBC](pt01ch09pyo04.md) 对象内部创建此对象的一个实例。该实例也由 [AccelerationBC](pt01ch09pyo04.md) 对象内部删除。

AccelerationBCState 对象没有构造函数或方法。

AccelerationBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.5.1 成员

AccelerationBCState 对象具有以下成员：

*a1*

一个 Float，指定 1 方向上的加速度分量。

*a2*

一个 Float，指定 2 方向上的加速度分量。

*a3*

一个 Float，指定 3 方向上的加速度分量。

*ar1*

一个 Float，指定关于 1 方向的旋转加速度分量。

*ar2*

一个 Float，指定关于 2 方向的旋转加速度分量。

*ar3*

一个 Float，指定关于 3 方向的旋转加速度分量。

*a1State*

一个 SymbolicConstant，指定 1 方向上加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*a2State*

一个 SymbolicConstant，指定 2 方向上加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*a3State*

一个 SymbolicConstant，指定 3 方向上加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ar1State*

一个 SymbolicConstant，指定关于 1 方向旋转加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ar2State*

一个 SymbolicConstant，指定关于 2 方向旋转加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ar3State*

一个 SymbolicConstant，指定关于 3 方向旋转加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*amplitudeState*

一个 SymbolicConstant，指定振幅引用的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*status*

一个 SymbolicConstant，指定 [BoundaryConditionState](pt01ch09pyo08.md) 对象的传播状态。可能的值为：
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- PROPAGATED_FROM_BASE_STATE
- MODIFIED_FROM_BASE_STATE
- DEACTIVATED_FROM_BASE_STATE
- BUILT_INTO_MODES

*amplitude*

一个 String，指定振幅引用的名称。如果边界条件没有振幅引用，则该 String 为空。

### 9.5.2 对应的分析关键字

| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary), TYPE=ACCELERATION (degree of freedom: 1, 2, 3, 4, 5, or 6) |
| --- |
