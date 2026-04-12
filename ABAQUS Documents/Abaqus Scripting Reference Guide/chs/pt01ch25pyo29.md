# 25.29 ElasticFoundationState 对象

ElasticFoundationState 对象在步骤中存储 [ElasticFoundation](pt01ch25pyo28.md) 对象的传播数据。ElasticFoundation 对象会为每个步骤内部创建一个此对象的实例。该实例也会由 ElasticFoundation 对象内部删除。

ElasticFoundationState 对象没有构造函数或方法。

ElasticFoundationState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.29.1 成员

ElasticFoundationState 对象具有以下成员：

*stiffness*

浮点数，指定每面积的基础刚度。

*stiffnessState*

 SymbolicConstant，指定刚度成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

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



