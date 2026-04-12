# 25.58 RadiationToAmbientState 对象

RadiationToAmbientState 对象在步骤中存储 [RadiationToAmbient](pt01ch25pyo57.md) 对象的传播数据。RadiationToAmbient 对象会为每个步骤内部创建一个此对象的实例。该实例也会由 RadiationToAmbient 对象内部删除。

RadiationToAmbientState 对象没有构造函数或方法。

RadiationToAmbientState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.58.1 成员

RadiationToAmbientState 对象具有以下成员：

*ambientTemperature*

浮点数，指定环境温度。

*ambientTemperatureState*

 SymbolicConstant，指定 *ambientTemperature* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*ambientTemperatureAmpState*

 SymbolicConstant，指定 *ambientTemperatureAmp* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*emissivity*

浮点数，指定发射率。

*emissivityState*

 SymbolicConstant，指定 *emissivity* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*ambientTemperatureAmp*

字符串，指定给出环境温度随时间变化的 Amplitude 对象的名称。

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

### 25.58.2 对应的分析关键字

| [*SRADIATE](../key/key-link.md#usb-kws-hsradiate) |
| --- |



