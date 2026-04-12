# 25.27 CyclicSymmetryState 对象

CyclicSymmetryState 对象存储 [CyclicSymmetry](pt01ch25pyo26.md) 对象的传播数据。CyclicSymmetry 对象会为每个步骤内部创建一个此对象的实例。该实例也会由 CyclicSymmetry 对象内部删除。

CyclicSymmetryState 对象没有构造函数或方法。

CyclicSymmetryState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.27.1 成员

CyclicSymmetryState 对象具有以下成员：

*extractedNodalDiameter*

 SymbolicConstant，指定 Abaqus 是否提取所有可能的节点直径或在 *lowestNodalDiameter* 和 *highestNodalDiameter* 用户指定值之间的节点直径。可能的值为 ALL_NODAL_DIAMETER 和 SPECIFIED_NODAL_DIAMETER。默认值为 ALL_NODAL_DIAMETER。

*extractedNodalDiameterState*

 SymbolicConstant，指定 *extractedNodalDiameter* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*lowestNodalDiameter*

整数，指定在特征频率分析中使用的最低节点直径。默认值为 0。

*lowestNodalDiameterState*

 SymbolicConstant，指定 *lowestNodalDiameter* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*highestNodalDiameter*

整数，指定在特征频率分析中使用的最高节点直径。此参数值应小于或等于扇区总数的一半。默认值为 0。

*highestNodalDiameterState*

 SymbolicConstant，指定 *highestNodalDiameter* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*excitiationNodalDiameter*

整数，指定将执行基于模态的稳态动态分析的节点直径。此值应大于或等于最低节点直径（由 *lowestNodalDiameter* 参数指定），且小于或等于最高节点直径（由 *highestNodalDiameter* 参数指定）。默认值为 0。

*excitiationNodalDiameterState*

 SymbolicConstant，指定 *excitiationNodalDiameter* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*status*

 SymbolicConstant，指定 [InteractionState](pt01ch25pyo49.md) 对象的传播状态。可能的值为：
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- BUILT_INTO_BASE_STATE

### 25.27.2 对应的分析关键字

| [*CLOAD](../key/key-link.md#usb-kws-hcload), CYCLIC MODE |
| --- |
| [*DLOAD](../key/key-link.md#usb-kws-hdload), CYCLIC MODE |
| [*DSLOAD](../key/key-link.md#usb-kws-hdsload), CYCLIC MODE |
| [*SELECT CYCLIC SYMMETRY MODES](../key/key-link.md#usb-kws-hselectcycsymmodes) |



