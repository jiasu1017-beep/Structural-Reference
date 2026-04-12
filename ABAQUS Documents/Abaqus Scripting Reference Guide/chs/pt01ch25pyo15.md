# 25.15 ConcentratedRadiationToAmbientState 对象

ConcentratedRadiationToAmbientState 对象存储 [ConcentratedRadiationToAmbient](pt01ch25pyo14.md) 对象的传播数据。ConcentratedRadiationToAmbient 对象会为每个步骤内部创建一个此对象的实例。该实例也会由 ConcentratedRadiationToAmbient 对象内部删除。

ConcentratedRadiationToAmbientState 对象没有构造函数或方法。

ConcentratedRadiationToAmbientState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.15.1 成员

ConcentratedRadiationToAmbientState 对象具有以下成员：

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

*nodalArea*

浮点数，指定应用集中辐射的节点关联的面积。

*nodalAreaState*

 SymbolicConstant，指定 *nodalArea* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

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

### 25.15.2 对应的分析关键字

| [*CRADIATE](../key/key-link.md#usb-kws-hcradiate) |
| --- |



