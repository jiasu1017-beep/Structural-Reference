# 25.13 ConcentratedFilmConditionState 对象

ConcentratedFilmConditionState 对象存储 [ConcentratedFilmCondition](pt01ch25pyo12.md) 对象的传播数据。该对象由 [ConcentratedFilmCondition](pt01ch25pyo12.md) 对象为每个步骤在内部创建一个实例。该实例也由 [ConcentratedFilmCondition](pt01ch25pyo12.md) 对象在内部删除。

ConcentratedFilmConditionState 对象没有构造函数或方法。

ConcentratedFilmConditionState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.13.1 成员

ConcentratedFilmConditionState 对象具有以下成员：

*interactionPropertyState*

SymbolicConstant，指定 *interactionProperty* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*sinkTemperature*

Float，指定沉温。

*sinkTemperatureState*

SymbolicConstant，指定 *sinkTemperature* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*sinkAmplitudeState*

SymbolicConstant，指定 *sinkAmplitude* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*filmCoeff*

Float，指定膜系数。

*filmCoeffState*

SymbolicConstant，指定 *filmCoeff* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*filmCoeffAmplitudeState*

SymbolicConstant，指定 *filmCoeffAmplitude* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*nodalArea*

Float，指定施加集中膜条件的节点相关面积。

*nodalAreaState*

SymbolicConstant，指定 *nodalArea* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*interactionProperty*

String，指定与此交互关联的 [FilmConditionProp](pt01ch25pyo32.md) 对象。

*sinkAmplitude*

String，指定给出沉温变化的 Amplitude 对象名称。

*filmCoeffAmplitude*

String，指定给出膜系数变化的 Amplitude 对象名称。

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

### 25.13.2 对应的分析关键字

| [*CFILM](../key/key-link.md#usb-kws-hcfilm) |
| --- |
