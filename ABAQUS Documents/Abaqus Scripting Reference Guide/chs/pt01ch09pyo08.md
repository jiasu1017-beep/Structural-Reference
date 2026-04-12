# 9.8 BoundaryConditionState 对象

BoundaryConditionState 对象是其他 BoundaryConditionState 对象的抽象基类型。BoundaryConditionState 对象没有显式构造函数或方法。BoundaryConditionState 对象的成员对所有派生自 BoundaryConditionState 对象的对象都是通用的。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.8.1 成员

BoundaryConditionState 对象具有以下成员：

*amplitudeState*

一个 SymbolicConstant，指定振幅引用的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*status*

一个 SymbolicConstant，指定 BoundaryConditionState 对象的传播状态。可能的值为：
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- PROPAGATED_FROM_BASE_STATE
- MODIFIED_FROM_BASE_STATE
- DEACTIVATED_FROM_BASE_STATE
- BUILT_INTO_MODES

*amplitude*

一个 String，指定振幅引用的名称。如果边界条件没有振幅引用，则该 String 为空。
