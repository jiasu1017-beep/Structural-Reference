# 25.26 CyclicSymmetry 对象

CyclicSymmetry 对象定义循环对称分析。

CyclicSymmetry 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.26.1 CyclicSymmetry(...)

此方法创建 CyclicSymmetry 对象。

**路径**

```
mdb.models[*name*].CyclicSymmetry
```

**必需参数**

*name*

String，指定存储库密钥。

*createStepName*

String，指定要创建循环对称交互的步骤名称。

*master*

[Region](pt01ch45pyo03.md) 对象，指定主表面。

*slave*

[Region](pt01ch45pyo03.md) 对象，指定从表面。

*repetitiveSectors*

Int，指定循环对称模型中的总扇区数。

*axisPoint1*

[Region](pt01ch45pyo03.md) 对象，指定对称轴的第一个点。该区域应恰好包含一个网格节点、顶点、插值点、参考点或基准点。在二维模型中，*axisPoint1* 是用于定义对称轴的唯一点。

*axisPoint2*

[Region](pt01ch45pyo03.md) 对象，指定对称轴的第二个点。该区域应恰好包含一个网格节点、顶点、插值点、参考点或基准点。在二维模型中，此点被忽略。

**可选参数**

*extractedNodalDiameter*

SymbolicConstant，指定 Abaqus 是否提取所有可能的节点直径，或介于 *lowestNodalDiameter* 和 *highestNodalDiameter* 用户指定值之间的节点直径。可能的值为 ALL_NODAL_DIAMETER 和 SPECIFIED_NODAL_DIAMETER。默认值为 ALL_NODAL_DIAMETER。

*lowestNodalDiameter*

Int，指定特征频率分析中使用的最低节点直径。默认值为 0。

*highestNodalDiameter*

Int，指定特征频率分析中使用的最高节点直径。此参数值应小于或等于总扇区数的一半（如 *repetitiveSectors* 参数中所指定）。默认值为 0。

*excitationNodalDiameter*

Int，指定将执行基于模态的稳态动态分析的节点直径。此值应大于或等于最低节点直径（在 *lowestNodalDiameter* 参数中指定），且小于或等于最高节点直径（在 *highestNodalDiameter* 参数中指定）。默认值为 0。

*adjustTie*

布尔值，指定是否调整循环对称的从表面以将其绑定到主表面。默认值为 ON。

*positionTolerance*

Float，指定位置容差。*positionTolerance* 参数仅在 *positionToleranceMethod*=SPECIFY_TOLERANCE 时适用。默认值为 0.0。

*positionToleranceMethod*

SymbolicConstant，指定用于确定位置容差的方法。可能的值为 COMPUTED_TOLERANCE 和 SPECIFY_TOLERANCE。默认值为 COMPUTED_TOLERANCE。

**返回值**

CyclicSymmetry 对象。

**异常**

无。

### 25.26.2 swapSurfaces()

此方法切换循环对称交互的主表面和从表面。此命令仅在创建交互的步骤中有效。

**参数**

无。

**返回值**

无。

**异常**

无。

### 25.26.3 setValues(...)

此方法修改在创建交互的步骤中现有 CyclicSymmetry 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CyclicSymmetry](pt01ch25pyo26.md#ker-cyclicsymmetry-cyclicsymmetry-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.26.4 setValuesInStep(...)

此方法修改在指定步骤中现有 CyclicSymmetry 对象的传播数据。

**必需参数**

*stepName*

String，指定要修改交互的步骤名称。

**可选参数**

*extractedNodalDiameter*

SymbolicConstant，指定 Abaqus 是否提取所有可能的节点直径，或介于 *lowestNodalDiameter* 和 *highestNodalDiameter* 用户指定值之间的节点直径。可能的值为 ALL_NODAL_DIAMETER 和 SPECIFIED_NODAL_DIAMETER。默认值为 ALL_NODAL_DIAMETER。

*lowestNodalDiameter*

Int，指定特征频率分析中使用的最低节点直径。默认值为 0。

*highestNodalDiameter*

Int，指定特征频率分析中使用的最高节点直径。此参数值应小于或等于总扇区数的一半（如 *repetitiveSectors* 参数中所指定）。默认值为 0。

*excitationNodalDiameter*

Int，指定将执行基于模态的稳态动态分析的节点直径。此值应大于或等于最低节点直径（在 *lowestNodalDiameter* 参数中指定），且小于或等于最高节点直径（在 *highestNodalDiameter* 参数中指定）。默认值为 0。

**返回值**

无。

**异常**

无。

### 25.26.5 成员

CyclicSymmetry 对象的成员与 [CyclicSymmetry](pt01ch25pyo26.md#ker-cyclicsymmetry-cyclicsymmetry-pyc) 方法的参数具有相同的名称和描述。

### 25.26.6 对应的分析关键字

| [*CLOAD](../key/key-link.md#usb-kws-hcload), CYCLIC MODE |
| --- |
| [*CYCLIC SYMMETRY MODEL](../key/key-link.md#usb-kws-mcycsymmodel) |
| [*DLOAD](../key/key-link.md#usb-kws-hdload), CYCLIC MODE |
| [*DSLOAD](../key/key-link.md#usb-kws-hdsload), CYCLIC MODE |
| [*SELECT CYCLIC SYMMETRY MODES](../key/key-link.md#usb-kws-hselectcycsymmodes) |
| [*TIE](../key/key-link.md#usb-kws-mtie), CYCLIC SYMMETRY |
