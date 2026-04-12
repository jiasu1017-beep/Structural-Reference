# 2.2 AdaptiveMeshConstraintState 对象





AdaptiveMeshConstraintState 对象是其他任意拉格朗日欧拉（ALE）样式 AdaptiveMeshConstraintState 对象的抽象基类型。AdaptiveMeshConstraintState 对象没有显式构造函数或方法。AdaptiveMeshConstraintState 对象的成员对从 AdaptiveMeshConstraintState 对象派生的所有对象都是通用的。

**访问**

```
import step
mdb.models[*name*].steps[*name*].adaptiveMeshConstraintStates[*name*]
```

### 2.2.1 成员

AdaptiveMeshConstraintState 对象具有以下成员：

*amplitudeState*

一个 SymbolicConstant，指定幅值参考的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*status*

一个 SymbolicConstant，指定 AdaptiveMeshConstraintState 对象的传播状态。可能的值为：
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

一个 String，指定幅值参考的名称。如果自适应网格约束没有幅值参考，则该 String 为空。





