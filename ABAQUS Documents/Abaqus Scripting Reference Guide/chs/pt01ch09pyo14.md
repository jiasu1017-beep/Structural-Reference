# 9.14 ConnDisplacementBCState 对象

ConnDisplacementBCState 对象存储步骤中连接器位移/旋转边界条件的传播数据。该对象由 [ConnDisplacementBC](pt01ch09pyo13.md) 对象为每个步骤内部创建一个实例。该实例也由 [ConnDisplacementBC](pt01ch09pyo13.md) 对象内部删除。

ConnDisplacementBCState 对象没有构造函数或方法。

ConnDisplacementBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.14.1 成员

ConnDisplacementBCState 对象具有以下成员：

*u1*

Float 或 Complex，指定连接器局部 1 方向的位移分量。

*u2*

Float 或 Complex，指定连接器局部 2 方向的位移分量。

*u3*

Float 或 Complex，指定连接器局部 3 方向的位移分量。

*ur1*

Float 或 Complex，指定连接器局部 4 方向的旋转分量。

*ur2*

Float 或 Complex，指定连接器局部 5 方向的旋转分量。

*ur3*

Float 或 Complex，指定连接器局部 6 方向的旋转分量。

*u1State*

SymbolicConstant，指定连接器局部 1 方向位移分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*u2State*

SymbolicConstant，指定连接器局部 2 方向位移分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*u3State*

SymbolicConstant，指定连接器局部 3 方向位移分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ur1State*

SymbolicConstant，指定连接器局部 4 方向旋转分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ur2State*

SymbolicConstant，指定连接器局部 5 方向旋转分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*ur3State*

SymbolicConstant，指定连接器局部 6 方向旋转分量的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

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

### 9.14.2 对应分析关键字

| [*CONNECTOR MOTION](../key/key-link.md#usb-kws-hconnectormotion)，TYPE=DISPLACEMENT（自由度：1、2、3、4、5 或 6）|
| --- |
