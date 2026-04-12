# 2.8 DisplacementAdaptiveMeshConstraintState 对象





DisplacementAdaptiveMeshConstraintState 对象存储步骤中任意拉格朗日欧拉（ALE）样式位移/旋转自适应网格约束的传播数据。DisplacementAdaptiveMeshConstraint 对象为每个步骤内部创建一个此对象的实例。DisplacementAdaptiveMeshConstraint 对象也会内部删除该实例。

DisplacementAdaptiveMeshConstraintState 对象没有构造函数或方法。

DisplacementAdaptiveMeshConstraintState 对象派生自 [AdaptiveMeshConstraintState](pt01ch02pyo02.md) 对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*].adaptiveMeshConstraintStates[*name*]
```

### 2.8.1 成员

DisplacementAdaptiveMeshConstraintState 对象具有以下成员：

*u1*

一个 Float 或 Complex，指定 1 方向的位移分量。

*u2*

一个 Float 或 Complex，指定 2 方向的位移分量。

*u3*

一个 Float 或 Complex，指定 3 方向的位移分量。

*ur1*

一个 Float 或 Complex，指定关于 1 方向的旋转位移分量。

*ur2*

一个 Float 或 Complex，指定关于 2 方向的旋转位移分量。

*ur3*

一个 Float 或 Complex，指定关于 3 方向的旋转位移分量。

*u1State*

一个 SymbolicConstant，指定 1 方向位移分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*u2State*

一个 SymbolicConstant，指定 2 方向位移分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*u3State*

一个 SymbolicConstant，指定 3 方向位移分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ur1State*

一个 SymbolicConstant，指定关于 1 方向旋转位移分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ur2State*

一个 SymbolicConstant，指定关于 2 方向旋转位移分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ur3State*

一个 SymbolicConstant，指定关于 3 方向旋转位移分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

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

### 2.8.2 对应分析关键字

| [*ADAPTIVE MESH CONSTRAINT](../key/key-link.md#usb-kws-hadaptivemeshconstraint), TYPE=DISPLACEMENT (自由度: 1, 2, 3, 4, 5 或 6) |
| --- |



