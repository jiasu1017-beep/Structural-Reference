# 9.37 PorePressureBCState 对象

PorePressureBCState 对象存储步骤中孔隙压力边界条件的传播数据。该对象由 [PorePressureBC](pt01ch09pyo36.md) 对象为每个步骤内部创建一个实例。该实例也由 [PorePressureBC](pt01ch09pyo36.md) 对象内部删除。

PorePressureBCState 对象没有构造函数或方法。

PorePressureBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.37.1 成员

PorePressureBCState 对象具有以下成员：

*magnitude*

Float，指定孔隙压力大小。

*magnitudeState*

SymbolicConstant，指定孔隙压力大小的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

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

### 9.37.2 对应分析关键字

| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary)（自由度：8）|
| --- |
