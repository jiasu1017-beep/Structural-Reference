# 9.3 AccelerationBaseMotionBCState 对象

AccelerationBaseMotionBCState 对象存储速度基准运动边界条件在步骤中的传播数据。系统为每个步骤由 [AccelerationBaseMotionBC](pt01ch09pyo02.md) 对象内部创建此对象的一个实例。该实例也由 [AccelerationBaseMotionBC](pt01ch09pyo02.md) 对象内部删除。

AccelerationBaseMotionBCState 对象没有构造函数或方法。

AccelerationBaseMotionBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.3.1 成员

AccelerationBaseMotionBCState 对象具有以下成员：

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

### 9.3.2 对应的分析关键字

| [*BASE MOTION](../key/key-link.md#usb-kws-hbasemotion) |
| --- |
