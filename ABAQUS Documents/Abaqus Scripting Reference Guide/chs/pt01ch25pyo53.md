# 25.53 NormalBehavior 对象

NormalBehavior 对象为接触交互属性指定法向行为。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].normalBehavior
```

### 25.53.1 NormalBehavior(...)

此方法创建一个 NormalBehavior 对象。

**路径**

```
mdb.models[*name*].interactionProperties[*name*].NormalBehavior
```

**必需参数**

无。

**可选参数**

*contactStiffness*

 SymbolicConstant DEFAULT 或浮点数，指定接触刚度。此参数适用于 *pressureOverclosure*=LINEAR。当 *pressureOverclosure*=HARD 且 *constraintEnforcementMethod*=AUGMENTED_LAGRANGE 或 PENALTY 时，此参数也有效。DEFAULT 值仅在满足后续条件时有效。零值等同于指定 DEFAULT。默认值为 DEFAULT。

*pressureOverclosure*

 SymbolicConstant，指定要使用的压力-过闭合关系。可能的值为 HARD、EXPONENTIAL、LINEAR、TABULAR 和 SCALE_FACTOR。默认值为 HARD。

*allowSeparation*

布尔值，指定是否允许接触后分离。默认值为 ON。

*maxStiffness*

 `None` 或浮点数，指定最大刚度。如果 *maxStiffness*=`None`，则没有上限。默认值为 `None`。

*table*

浮点数序列的序列，指定法向行为属性。此参数仅在 *pressureOverclosure*=EXPONENTIAL 或 TABULAR 时有效。表格数据中的项目在下面描述。

*constraintEnforcementMethod*

 SymbolicConstant，指定接触约束的强制方法。可能的值为 DEFAULT、AUGMENTED_LAGRANGE、PENALTY 和 DIRECT。默认值为 DEFAULT。

*overclosureFactor*

浮点数，指定过闭合度量（用于划分压力-过闭合曲线的段），作为接触区域中最小元素尺寸的百分比。默认值为 0.0。

*overclosureMeasure*

浮点数，指定过闭合度量（用于划分压力-过闭合曲线的段）直接。默认值为 0.0。

*contactStiffnessScaleFactor*

浮点数，指定惩罚刚度的比例因子或"基础"刚度的几何缩放。默认值为 1.0。

*initialStiffnessScaleFactor*

浮点数，指定"基础"默认接触刚度的额外比例因子。默认值为 1.0。

*clearanceAtZeroContactPressure*

浮点数，指定接触压力为零时的间隙。默认值为 0.0。

*stiffnessBehavior*

 SymbolicConstant，指定要定义的惩罚刚度类型。此参数仅在 *constraintEnforcementMethod*=PENALTY 时有效。可能的值为 LINEAR 和 NONLINEAR。默认值为 LINEAR。

*stiffnessRatio*

浮点数，指定初始刚度除以最终刚度的比值。此参数仅在 *stiffnessBehavior*=NONLINEAR 时有效。可能的值为 0 ![](../graphics/ker_eqn00013.gif) *stiffnessRatio* ![](../graphics/ker_eqn00048.gif) 1。默认值为 0.01。

*upperQuadraticFactor*

浮点数，指定最大刚度处的过闭合与特征面元长度之比。此参数仅在 *stiffnessBehavior*=NONLINEAR 时有效。默认值为 0.03。

*lowerQuadraticRatio*

浮点数，指定初始刚度处的过闭合与最大刚度处的过闭合之比，两者均相对于接触压力为零时的间隙。此参数仅在 *stiffnessBehavior*=NONLINEAR 时有效。可能的值为 0 ![](../graphics/ker_eqn00013.gif) *stiffnessRatio* ![](../graphics/ker_eqn00048.gif) 1。默认值为 0.33333。

**表格数据**

如果 *pressureOverclosure*=EXPONENTIAL，表格数据指定以下内容：
- 零间隙时的压力，![](../graphics/ker_eqn00079.gif)。
- 接触压力为零时的间隙，![](../graphics/ker_eqn00080.gif)。

如果 *pressureOverclosure*=TABULAR，表格数据指定以下内容：
- 压力。
- 过闭合。

**返回值**

NormalBehavior 对象。

**异常**

无。

### 25.53.2 setValues(...)

此方法修改 NormalBehavior 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [NormalBehavior](pt01ch25pyo53.md#ker-normalbehavior-normalbehavior-pyc) 方法的参数相同。

**返回值**

无。

**异常**

无。

### 25.53.3 成员

NormalBehavior 对象的成员与 [NormalBehavior](pt01ch25pyo53.md#ker-normalbehavior-normalbehavior-pyc) 方法的参数具有相同的名称和描述。

### 25.53.4 对应的分析关键字

| [*SURFACE BEHAVIOR](../key/key-link.md#usb-kws-hsurfacebehavior) |
| --- |



