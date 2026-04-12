# 9.44 TemperatureBCState 对象

TemperatureBCState 对象存储步骤中温度边界条件的传播数据。该对象由 [TemperatureBC](pt01ch09pyo43.md) 对象为每个步骤内部创建一个实例。该实例也由 [TemperatureBC](pt01ch09pyo43.md) 对象内部删除。

TemperatureBCState 对象没有构造函数或方法。

TemperatureBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.44.1 成员

TemperatureBCState 对象具有以下成员：

*magnitude*

Float，指定温度大小。

*magnitudeState*

SymbolicConstant，指定温度大小的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*dofState*

SymbolicConstant，指定 *dof*成员的传播状态。可能的值为 SET 和 UNCHANGED。

*dof*

Int 的元组，指定边界条件所应用到的自由度。

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

### 9.44.2 对应分析关键字

| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary)（实体自由度：11；壳自由度：11、12 等）|
| --- |
