# 42.12 PredefinedFieldState 对象

PredefinedFieldState 对象是 [Step](pt01ch49pyo01.md) 对象的 `predefinedFieldState` 存储库中对象的基对象。PredefinedFieldState 对象的成员对从 PredefinedFieldState 派生的所有对象通用。

PredefinedFieldState 对象没有构造函数或方法。

**访问**

```
import load
mdb.models[*name*].steps[*name*].predefinedFieldStates[*name*]
```

### 42.12.1 成员

PredefinedFieldState 对象具有以下成员：

*status*

 SymbolicConstant，指定 PredefinedFieldState 对象的传播状态。可选值为：
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- DEACTIVATED_TO_INITIAL
- NO_LONGER_ACTIVE
- RESET_TO_INITIAL
- TO_BE_COMPUTED
- PROPAGATED_FROM_COMPUTED
- BUILT_INTO_BASE_STATE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE

此成员存在于所有 PredefinedFieldState 对象中，但不同的预定义场根据传播规则使用整个可能值列表的不同子集。

