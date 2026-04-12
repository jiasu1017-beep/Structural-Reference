# 9.12 ConnAccelerationBCState 对象

ConnAccelerationBCState 对象存储步骤中连接器加速度边界条件的传播数据。该对象由 [ConnAccelerationBC](pt01ch09pyo11.md) 对象为每个步骤内部创建一个实例。该实例也由 [ConnAccelerationBC](pt01ch09pyo11.md) 对象内部删除。

ConnAccelerationBCState 对象没有构造函数或方法。

ConnAccelerationBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.12.1 成员

ConnAccelerationBCState 对象具有以下成员：

*a1*

Float，指定连接器局部 1 方向的连接器加速度分量。

*a2*

Float，指定连接器局部 2 方向的连接器加速度分量。

*a3*

Float，指定连接器局部 3 方向的连接器加速度分量。

*ar1*

Float，指定连接器局部 4 方向的连接器加速度分量。

*ar2*

Float，指定连接器局部 5 方向的连接器加速度分量。

*ar3*

Float，指定连接器局部 6 方向的连接器加速度分量。

*a1State*

SymbolicConstant，指定连接器局部 1 方向的连接器加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*a2State*

SymbolicConstant，指定连接器局部 2 方向的连接器加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*a3State*

SymbolicConstant，指定连接器局部 3 方向的连接器加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ar1State*

SymbolicConstant，指定连接器局部 4 方向的连接器加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ar2State*

SymbolicConstant，指定连接器局部 5 方向的连接器加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ar3State*

SymbolicConstant，指定连接器局部 6 方向的连接器加速度分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

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

### 9.12.2 对应分析关键字

| [*CONNECTOR MOTION](../key/key-link.md#usb-kws-hconnectormotion)，TYPE=ACCELERATION（自由度：1、2、3、4、5 或 6）|
| --- |
