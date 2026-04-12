# 25.49 InteractionState 对象

InteractionState 对象是其他 InteractionState 对象的抽象基类型。InteractionState 对象没有构造函数。InteractionState 对象的成员是从 InteractionState 派生的所有对象共有的。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.49.1 成员

InteractionState 对象具有以下成员：

*status*

 SymbolicConstant，指定 InteractionState 对象的传播状态。可能的值为：
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- BUILT_INTO_BASE_STATE



