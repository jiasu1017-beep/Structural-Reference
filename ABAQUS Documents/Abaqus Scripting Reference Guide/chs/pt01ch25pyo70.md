# 25.70 StdXplCosimulationState 对象

StdXplCosimulationState 对象在步骤中存储 [StdXplCosimulation](pt01ch25pyo69.md) 对象的传播数据。StdXplCosimulation 对象会为每个步骤内部创建一个此对象的实例。该实例也会由 StdXplCosimulation 对象内部删除。

StdXplCosimulationState 对象没有构造函数或方法。

StdXplCosimulationState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.70.1 成员

StdXplCosimulationState 对象具有以下成员：

*status*

 SymbolicConstant，指定 [InteractionState](pt01ch25pyo49.md) 对象的传播状态。可能的值为：
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- BUILT_INTO_BASE_STATE

### 25.70.2 对应的分析关键字

| [*CO-SIMULATION](../key/key-link.md#usb-kws-hcosimulation), |
| --- |
| [*CO-SIMULATION REGION](../key/key-link.md#usb-kws-hcosimulationregion), |
| [*CO-SIMULATION CONTROLS](../key/key-link.md#usb-kws-hcosimulationcontrols) |



