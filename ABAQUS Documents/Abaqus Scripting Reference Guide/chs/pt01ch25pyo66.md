# 25.66 StdContactControl 对象

StdContactControl 对象在 Abaqus/Standard 分析中用于指定涉及物体之间接触的问题的可选解控制。

StdContactControl 对象派生自 [ContactControl](pt01ch25pyo16.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].contactControls[*name*]
```

### 25.66.1 StdContactControl(...)

此方法创建一个 StdContactControl 对象。

**路径**

```
mdb.models[*name*].StdContactControl
```

**必需参数**

*name*

字符串，指定接触控制存储库键。

**可选参数**

*stiffnessScaleFactor*

浮点数，指定 Abaqus/Standard 缩放默认惩罚刚度的因子，以获得用于接触对的刚度。只有使用增强拉格朗日表面行为定义的接触交互会受到此参数的影响。默认值为 1.0。

*penetrationTolChoice*

 SymbolicConstant，指定允许渗透是绝对值还是相对于特征接触表面面元尺寸的值。只有使用增强拉格朗日表面行为定义的接触交互会受到此参数的影响。可能的值为 RELATIVE 和 ABSOLUTE。默认值为 RELATIVE。

*relativePenetrationTolerance*

浮点数，指定允许渗透与特征接触表面面元尺寸的比率。浮点值表示百分比（例如：0.001=0.1%）。只有使用增强拉格朗日表面行为定义的接触交互会受到此参数的影响。默认值为 10–3。

*relativePenetrationTolerance* 参数仅在 *penetrationTolChoice*=RELATIVE 时适用。*relativePenetrationTolerance* 和 *absolutePenetrationTolerance* 参数互斥。

*absolutePenetrationTolerance*

 `None` 或浮点数，指定允许渗透。只有使用增强拉格朗日表面行为定义的接触交互会受到此参数的影响。*absolutePenetrationTolerance* 参数仅在 *penetrationTolChoice*=ABSOLUTE 时适用。*relativePenetrationTolerance* 和 *absolutePenetrationTolerance* 参数互斥。默认值为 `None`。

*frictionOnset*

 SymbolicConstant，指定何时应用摩擦。可能的值为：
- IMMEDIATE，指定摩擦包含在接触发生的增量中。
- DELAYED，指定摩擦的应用延迟到接触发生后的增量。

默认值为 IMMEDIATE。

*automaticTolerances*

布尔值，指定 Abaqus/Standard 是否应自动计算过闭合容差和分离容差以防止接触中的抖动。默认值为 OFF。

*automaticTolerances* 参数不能与 *maxchp*、*perrmx* 和 *uerrmx* 参数一起使用。

*maxchp*

整数，指定在任何增量中允许违反接触条件的最大点数。默认值为 0。

必须同时指定 *perrmx* 或 *uerrmx* 参数与 *maxchp* 参数。

*perrmx*

浮点数，指定在接触点传输的允许拉伸应力（拉伸力在 GAP- 或 ITT 型接触元素中）的最大值。默认值为 0.0。

*perrmx* 参数必须与 *maxchp* 参数一起指定。

*uerrmx*

浮点数，指定被视为开放的从属节点允许的最大过闭合距离。默认值为 0.0。

*uerrmx* 参数必须与 *maxchp* 参数一起指定。

*stabilizeChoice*

 SymbolicConstant，指定是否指定粘性阻尼，如果指定，如何指定。可能的值为 NONE、AUTOMATIC 和 COEFFICIENT。默认值为 NONE。

*dampFactor*

浮点数，指定阻尼因子的值。此值乘以计算的阻尼系数。默认值为 1.0。

此参数仅在 *stabilizeChoice*=AUTOMATIC 时有效。

*dampCoef*

浮点数，指定阻尼系数。默认值为 0.0。

此参数仅在 *stabilizeChoice*=COEFFICIENT 时有效。

*tangFraction*

浮点数，指定切向稳定化作为法向稳定化（阻尼）的分数。默认值为 1.0。

此参数仅在 *stabilizeChoice* = AUTOMATIC 或 COEFFICIENT 时有效。

*eosFraction*

浮点数，指定在步骤结束时保持的阻尼比例。默认值为 0.0。

此参数仅在 *stabilizeChoice* = AUTOMATIC 或 COEFFICIENT 时有效。

*zeroDampingChoice*

 SymbolicConstant，指定如何指定零阻尼间隙。可能的值为 COMPUTE 和 SPECIFY。默认值为 COMPUTE。

此参数仅在 *stabilizeChoice* = AUTOMATIC 或 COEFFICIENT 时有效。

*zeroDamping*

 `None` 或浮点数，指定阻尼变为零的间隙。此参数仅在 *zeroDampingChoice*=SPECIFY 时有效。此参数仅在 *stabilizeChoice* = AUTOMATIC 或 COEFFICIENT 时有效。默认值为 `None`。

*enforceWithLagrangeMultipliers*

 SymbolicConstant，指定是否用拉格朗日乘子强制接触约束。可能的值为 DEFAULT、ENFORCEMENT_OFF 和 ENFORCEMENT_ON。默认值为 DEFAULT。

**返回值**

StdContactControl 对象。

**异常**

RangeError。

### 25.66.2 setValues(...)

此方法修改 StdContactControl 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [StdContactControl](pt01ch25pyo66.md#ker-stdcontactcontrol-stdcontactcontrol-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 25.66.3 成员

StdContactControl 对象的成员与 [StdContactControl](pt01ch25pyo66.md#ker-stdcontactcontrol-stdcontactcontrol-pyc) 方法的参数具有相同的名称和描述。

### 25.66.4 对应的分析关键字

| [*CONTACT CONTROLS](../key/key-link.md#usb-kws-hcontactcontrols) |
| --- |



