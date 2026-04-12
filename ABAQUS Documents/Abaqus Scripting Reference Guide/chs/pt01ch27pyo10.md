# 27.10 BodyForceState 对象





BodyForceState 对象存储体力在某个步骤中的传播数据。该对象的实例由 [BodyForce](pt01ch27pyo09.md) 对象为每个步骤内部创建。该实例也由 [BodyForce](pt01ch27pyo09.md) 对象内部删除。

BodyForceState 对象没有构造函数或方法。

BodyForceState 对象派生自 [LoadState](pt01ch27pyo42.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.10.1 成员

BodyForceState 对象具有以下成员：

*comp1*

一个 Float 或 Complex，指定 1 方向上的体力分量。

*comp2*

一个 Float 或 Complex，指定 2 方向上的体力分量。

*comp3*

一个 Float 或 Complex，指定 3 方向上的体力分量。

*comp1State*

一个 SymbolicConstant，指定 1 方向上体力分量的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 MODIFIED。

*comp2State*

一个 SymbolicConstant，指定 2 方向上体力分量的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 MODIFIED。

*comp3State*

一个 SymbolicConstant，指定 3 方向上体力分量的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 MODIFIED。

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

### 27.10.2 对应的分析关键字

| [*DLOAD](../key/key-link.md#usb-kws-hdload) (载荷类型标签: BX, BY, BZ, BR, BXNU, BYNU, BZNU, 或 BRNU) |
| --- |




