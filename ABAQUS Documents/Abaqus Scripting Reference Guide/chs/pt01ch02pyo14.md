# 2.14 VelocityAdaptiveMeshConstraintState 对象





VelocityAdaptiveMeshConstraintState 对象存储步骤中任意拉格朗日欧拉（ALE）样式速度自适应网格约束的传播数据。VelocityAdaptiveMeshConstraint 对象为每个步骤内部创建一个此对象的实例。VelocityAdaptiveMeshConstraint 对象也会内部删除该实例。

VelocityAdaptiveMeshConstraintState 对象没有构造函数或方法。

VelocityAdaptiveMeshConstraintState 对象派生自 [AdaptiveMeshConstraintState](pt01ch02pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*].adaptiveMeshConstraintStates[*name*]
```

### 2.14.1 成员

VelocityAdaptiveMeshConstraintState 对象具有以下成员：

*v1*

一个 Float，指定 1 方向的速度分量。

*v2*

一个 Float，指定 2 方向的速度分量。

*v3*

一个 Float，指定 3 方向的速度分量。

*vr1*

一个 Float，指定关于 1 方向的速度分量。

*vr2*

一个 Float，指定关于 2 方向的速度分量。

*vr3*

一个 Float，指定关于 3 方向的速度分量。

*v1State*

一个 SymbolicConstant，指定 1 方向速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*v2State*

一个 SymbolicConstant，指定 2 方向速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*v3State*

一个 SymbolicConstant，指定 3 方向速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*vr1State*

一个 SymbolicConstant，指定关于 1 方向速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*vr2State*

一个 SymbolicConstant，指定关于 2 方向速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*vr3State*

一个 SymbolicConstant，指定关于 3 方向速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*amplitudeState*

一个 SymbolicConstant，指定幅值参考的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*status*

一个 SymbolicConstant，指定 [AdaptiveMeshConstraintState](pt01ch02pyo02.md) 对象的传播状态。可能的值为：
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

### 2.14.2 对应分析关键字

| [*ADAPTIVE MESH CONSTRAINT](../key/key-link.md#usb-kws-hadaptivemeshconstraint), TYPE=VELOCITY (自由度: 1, 2, 3, 4, 5 或 6) |
| --- |



