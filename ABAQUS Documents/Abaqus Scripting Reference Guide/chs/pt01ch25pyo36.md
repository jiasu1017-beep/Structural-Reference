# 25.36 FluidCavityState 对象

FluidCavityState 对象存储 [FluidCavity](pt01ch25pyo34.md) 对象的传播数据。FluidCavity 对象会为每个步骤内部创建一个此对象的实例。该实例也会由 FluidCavity 对象内部删除。

FluidCavityState 对象没有构造函数或方法。

FluidCavityState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.36.1 成员

FluidCavityState 对象具有以下成员：

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



