# 25.33 FilmConditionState 对象

FilmConditionState 对象在步骤中存储 [FilmCondition](pt01ch25pyo31.md) 对象的传播数据。FilmCondition 对象会为每个步骤内部创建一个此对象的实例。该实例也会由 FilmCondition 对象内部删除。

FilmConditionState 对象没有构造函数或方法。

FilmConditionState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.33.1 成员

FilmConditionState 对象具有以下成员：

*interactionPropertyState*

 SymbolicConstant，指定 *interactionProperty* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*sinkTemperature*

浮点数，指定汇温度。

*sinkTemperatureState*

 SymbolicConstant，指定 *sinkTemperature* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*sinkAmplitudeState*

 SymbolicConstant，指定 *sinkAmplitude* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*filmCoeff*

浮点数，指定膜系数。

*filmCoeffState*

 SymbolicConstant，指定 *filmCoeff* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*filmCoeffAmplitudeState*

 SymbolicConstant，指定 *filmCoeffAmplitude* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*interactionProperty*

字符串，指定与此交互关联的 [FilmConditionProp](pt01ch25pyo32.md) 对象。

*sinkAmplitude*

字符串，指定给出汇温度随时间变化的 Amplitude 对象的名称。

*filmCoeffAmplitude*

字符串，指定给出膜系数随时间变化的 Amplitude 对象的名称。

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

### 25.33.2 对应的分析关键字

| [*SFILM](../key/key-link.md#usb-kws-hsfilm) |
| ---