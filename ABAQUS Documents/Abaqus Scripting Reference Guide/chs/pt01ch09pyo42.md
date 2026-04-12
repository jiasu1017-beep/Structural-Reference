# 9.42 SubmodelBCState 对象

SubmodelBCState 对象存储步骤中子模型边界条件的传播数据。该对象由 [SubmodelBC](pt01ch09pyo41.md) 对象为每个步骤内部创建一个实例。该实例也由 [SubmodelBC](pt01ch09pyo41.md) 对象内部删除。

SubmodelBCState 对象没有构造函数或方法。

SubmodelBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.42.1 成员

SubmodelBCState 对象具有以下成员：

*dofState*

SymbolicConstant，指定 *dof*成员的传播状态。可能的值为 SET 和 UNCHANGED。

*globalStepState*

SymbolicConstant，指定 *globalStep*成员的传播状态。可能的值为 SET 和 UNCHANGED。

*globalIncrement*

Int，指定全局模型步骤中其解将用于指定驱动变量的值的增量号。此参数仅适用于线性扰动步骤。

*globalIncrementState*

SymbolicConstant，指定 *globalIncrement*成员的传播状态。可能的值为 SET 和 UNCHANGED。

*centerZoneSize*

`None` 或 Float，指定壳中面周围中心区域厚度。默认值为 `None`。

*centerZoneSizeState*

SymbolicConstant，指定 *centerZoneSize*成员的传播状态。可能的值为 SET 和 UNCHANGED。

*scale*

`None` 或 Float，指定施加在界面处的位移所应用的比例值。默认值为 1.0。

*scaleState*

SymbolicConstant，指定 *scale*成员的传播状态。可能的值为 SET 和 UNCHANGED。

*globalStep*

String，指定全局模型中的步骤，Abaqus 从该步骤读取将驱动子模型分析的变量值。String 表示分析步骤序列中的位置。例如，*globalStep*='1' 表示第一个步骤。

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

### 9.42.2 对应分析关键字

| [*SUBMODEL](../key/key-link.md#usb-kws-msubmodel)|
| --- |
| [*BOUNDARY](../key/key-link.md#usb-kws-hboundary)，SUBMODEL|
