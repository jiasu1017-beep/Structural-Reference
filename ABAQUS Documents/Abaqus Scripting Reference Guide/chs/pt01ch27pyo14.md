# 27.14 BoltLoadState 对象





BoltLoadState 对象存储螺栓载荷在某个步骤中的传播数据。该对象的实例由 [BoltLoad](pt01ch27pyo13.md) 对象为每个步骤内部创建。该实例也由 [BoltLoad](pt01ch27pyo13.md) 对象内部删除。

BoltLoadState 对象没有构造函数或方法。

BoltLoadState 对象派生自 [LoadState](pt01ch27pyo42.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].loadStates[*name*]
```

### 27.14.1 成员

BoltLoadState 对象具有以下成员：

*boltMethod*

一个 SymbolicConstant，指定螺栓载荷的类型。可能的值为 APPLY_FORCE、ADJUST_LENGTH 和 FIX_LENGTH。

*boltMethodState*

一个 SymbolicConstant，指定螺栓载荷类型的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 MODIFIED。

*magnitude*

一个 Float，指定螺栓载荷大小。

*magnitudeState*

一个 SymbolicConstant，指定螺栓载荷大小的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 MODIFIED。

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

### 27.14.2 对应的分析关键字

| [*CLOAD](../key/key-link.md#usb-kws-hcload) (当 *boltMethod*=APPLY_FORCE 时) |
| --- |
| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary) (当 *boltMethod*=ADJUST_LENGTH 或 FIX_LENGTH 时) |




