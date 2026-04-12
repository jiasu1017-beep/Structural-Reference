# 9.7 AcousticPressureBCState 对象

AcousticPressureBCState 对象存储声压边界条件在步骤中的传播数据。系统为每个步骤由 [AcousticPressureBC](pt01ch09pyo06.md) 对象内部创建此对象的一个实例。该实例也由 [AcousticPressureBC](pt01ch09pyo06.md) 对象内部删除。

AcousticPressureBCState 对象没有构造函数或方法。

AcousticPressureBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.7.1 成员

AcousticPressureBCState 对象具有以下成员：

*magnitude*

一个 Float，指定声压幅值。

*magnitudeState*

一个 SymbolicConstant，指定声压幅值的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

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

### 9.7.2 对应的分析关键字

| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary) (degree of freedom: 8) |
| --- |
