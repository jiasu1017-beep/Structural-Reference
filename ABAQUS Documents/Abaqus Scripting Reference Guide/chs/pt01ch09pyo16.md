# 9.16 ConnVelocityBCState 对象

ConnVelocityBCState 对象存储步骤中速度边界条件的传播数据。该对象由 [ConnVelocityBC](pt01ch09pyo15.md) 对象为每个步骤内部创建一个实例。该实例也由 [ConnVelocityBC](pt01ch09pyo15.md) 对象内部删除。

ConnVelocityBCState 对象没有构造函数或方法。

ConnVelocityBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.16.1 成员

ConnVelocityBCState 对象具有以下成员：

*v1*

Float，指定连接器局部 1 方向的速度分量。

*v2*

Float，指定连接器局部 2 方向的速度分量。

*v3*

Float，指定连接器局部 3 方向的速度分量。

*vr1*

Float，指定连接器局部 4 方向的旋转速度分量。

*vr2*

Float，指定连接器局部 5 方向的旋转速度分量。

*vr3*

Float，指定连接器局部 6 方向的旋转速度分量。

*v1State*

SymbolicConstant，指定连接器局部 1 方向速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*v2State*

SymbolicConstant，指定连接器局部 2 方向速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*v3State*

SymbolicConstant，指定连接器局部 3 方向速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*vr1State*

SymbolicConstant，指定连接器局部 4 方向旋转速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*vr2State*

SymbolicConstant，指定连接器局部 5 方向旋转速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*vr3State*

SymbolicConstant，指定连接器局部 6 方向旋转速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*amplitudeState*

SymbolicConstant，指定幅值引用的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*status*

SymbolicConstant，指定 [BoundaryConditionState](pt01ch09pyo08.md) 对象的传播状态。可能的值为：
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

String，指定幅值引用的名称。如果边界条件没有幅值引用，则 String 为空。

### 9.16.2 对应分析关键字

| [*CONNECTOR MOTION](../key/key-link.md#usb-kws-hconnectormotion)，TYPE=VELOCITY（自由度：1、2、3、4、5 或 6）|
| --- |
