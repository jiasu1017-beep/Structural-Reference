# 27.5 BodyConcentrationFluxState 对象

BodyConcentrationFluxState 对象存储 [BodyConcentrationFlux](pt01ch27pyo04.md) 对象在步骤中的传播数据。该对象由 [BodyConcentrationFlux](pt01ch27pyo04.md) 对象为每个步骤在内部创建一个实例。该实例也由 [BodyConcentrationFlux](pt01ch27pyo04.md) 对象在内部删除。

BodyConcentrationFluxState 对象没有构造函数或方法。

BodyConcentrationFluxState 对象派生自 [LoadState](pt01ch27pyo42.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.5.1 成员

BodyConcentrationFluxState 对象具有以下成员：

*magnitude*

Float，指定主体浓度通量大小。

*magnitudeState*

SymbolicConstant，指定主体浓度通量大小的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 MODIFIED。

*amplitudeState*

SymbolicConstant，指定 *amplitude* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*status*

SymbolicConstant，指定 [LoadState](pt01ch27pyo42.md) 对象的传播状态。可能的值为：
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- BUILT_INTO_BASE_STATE

*amplitude*

String，指定幅值参考的名称。如果载荷没有幅值参考，则该字符串为空。

### 27.5.2 对应的分析关键字

| [*CFLUX](../key/key-link.md#usb-kws-hcflux) |
| --- |
