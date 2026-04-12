# 27.12 BodyHeatFluxState 对象





BodyHeatFluxState 对象存储 [BodyHeatFlux](pt01ch27pyo11.md) 对象在某个步骤中的传播数据。该对象的实例由 [BodyHeatFlux](pt01ch27pyo11.md) 对象为每个步骤内部创建。该实例也由 [BodyHeatFlux](pt01ch27pyo11.md) 对象内部删除。

BodyHeatFluxState 对象没有构造函数或方法。

BodyHeatFluxState 对象派生自 [LoadState](pt01ch27pyo42.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.12.1 成员

BodyHeatFluxState 对象具有以下成员：

*magnitude*

一个 Float，指定体热通量大小。

*magnitudeState*

一个 SymbolicConstant，指定体热通量大小的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 MODIFIED。

*amplitudeState*

一个 SymbolicConstant，指定 *amplitude*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*status*

一个 SymbolicConstant，指定 [LoadState](pt01ch27pyo42.md) 对象的传播状态。可能的值为：
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

一个 String，指定幅值参考的名称。如果载荷没有幅值参考，则该 String 为空。

### 27.12.2 对应的分析关键字

| [*DFLUX](../key/key-link.md#usb-kws-hdflux) |
| --- |




