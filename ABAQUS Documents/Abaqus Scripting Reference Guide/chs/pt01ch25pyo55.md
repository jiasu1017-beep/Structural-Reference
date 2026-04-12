# 25.55 PressurePenetrationState 对象

PressurePenetrationState 对象存储 [PressurePenetration](pt01ch25pyo54.md) 对象在步骤中的传播数据。该对象由 [PressurePenetration](pt01ch25pyo54.md) 对象为每个步骤在内部创建一个实例。该实例也由 [PressurePenetration](pt01ch25pyo54.md) 对象在内部删除。

PressurePenetrationState 对象没有构造函数或方法。

PressurePenetrationState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.55.1 成员

PressurePenetrationState 对象具有以下成员：

*penetrationTime*

Float，指定当前步骤时间的一部分，在该时间内新渗透的接触面段的流体压力线性增加到当前大小。默认值为 10–3。

*penetrationTimeState*

SymbolicConstant，指定 *penetrationTime* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*amplitudeState*

SymbolicConstant，指定 *amplitude* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*criticalPressureState*

SymbolicConstant，指定 *criticalPressure* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*penetrationPressureState*

SymbolicConstant，指定 *penetrationPressure* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*penetrationPressure*

Float 元组，指定流体压力大小。对于稳态动态分析，指定流体压力大小的 Complex 元组。

*amplitude*

String，指定幅值参考的名称。如果载荷没有幅值参考，则该字符串为空。

*criticalPressure*

Float 元组，指定临界接触压力，低于该压力时流体渗透开始发生。

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

### 25.55.2 对应的分析关键字

| [*PRESSURE PENETRATION](../key/key-link.md#usb-kws-hpressurepenetration) |
| --- |
