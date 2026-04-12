# 25.25 ContactTangentialBehavior 对象

ContactTangentialBehavior 对象为接触交互属性指定切向行为。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].tangentialBehavior
```

### 25.25.1 TangentialBehavior(...)

此方法创建一个 ContactTangentialBehavior 对象。

**路径**

```
mdb.models[*name*].interactionProperties[*name*].TangentialBehavior
```

**必需参数**

无。

**可选参数**

*formulation*

 SymbolicConstant，指定摩擦公式。可能的值为 FRICTIONLESS、PENALTY、EXPONENTIAL_DECAY、ROUGH、LAGRANGE 和 USER_DEFINED。默认值为 FRICTIONLESS。

*directionality*

 SymbolicConstant，指定摩擦的方向性。可能的值为 ISOTROPIC 和 ANISOTROPIC。默认值为 ISOTROPIC。

*slipRateDependency*

布尔值，指定数据是否依赖于滑移率。默认值为 OFF。

*pressureDependency*

布尔值，指定数据是否依赖于接触压力。默认值为 OFF。

*temperatureDependency*

布尔值，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

整数，指定场变量的数量。默认值为 0。

*exponentialDecayDefinition*

 SymbolicConstant，指定指数衰减定义。可能的值为 COEFFICIENTS 和 TEST_DATA。默认值为 COEFFICIENTS。

*table*

浮点数序列的序列，指定切向行为。表格数据中的项目在下面描述。

*shearStressLimit*

 `None` 或浮点数，指定剪切应力极限。如果 *shearStressLimit*=`None`，则没有上限。默认值为 `None`。

*maximumElasticSlip*

 SymbolicConstant，指定最大弹性滑移将是什么。可能的值为 FRACTION 和 ABSOLUTE_DISTANCE。默认值为 FRACTION。

*fraction*

浮点数，指定特征表面尺寸的分数。默认值为 0.0。

*absoluteDistance*

浮点数，指定绝对距离。默认值为 0.0。

*elasticSlipStiffness*

 `None` 或浮点数，指定弹性滑移刚度。如果 *elasticSlipStiffness*=`None`，则没有上限。默认值为 `None`。

*nStateDependentVars*

整数，指定状态相关变量的数量。默认值为 0。

*useProperties*

布尔值，指定是否使用属性值。默认值为 OFF。

**表格数据**

如果 *formulation*=PENALTY 或 LAGRANGE，表格数据指定以下内容：
- 第一个滑移方向的摩擦系数，![](../graphics/ker_eqn00070.gif)。
- 第二个滑移方向的摩擦系数，![](../graphics/ker_eqn00071.gif)（如果 *directionality*=ANISOTROPIC）。
- 滑移率（如果数据依赖于滑移率）。
- 接触压力（如果数据依赖于接触压力）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *formulation*=EXPONENTIAL_DECAY 且 *exponentialDecayDefinition*=COEFFICIENTS，表格数据指定以下内容：
- 静摩擦系数。
- 动摩擦系数。
- 衰减系数。

如果 *formulation*=EXPONENTIAL_DECAY 且 *exponentialDecayDefinition*=TEST_DATA，表格数据指定以下内容：
- 摩擦系数。
- 滑移率。

如果 *formulation*=USER_DEFINED，表格数据指定以下内容：
- 摩擦属性。

**返回值**

ContactTangentialBehavior 对象。

**异常**

无。

### 25.25.2 setValues(...)

此方法修改 ContactTangentialBehavior 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ContactTangentialBehavior](pt01ch25pyo25.md#ker-contacttangentialbehavior-tangentialbehavior-pyc) 方法的参数相同。

**返回值**

无。

**异常**

无。

### 25.25.3 成员

ContactTangentialBehavior 对象具有以下成员：

*formulation*

 SymbolicConstant，指定摩擦公式。可能的值为 FRICTIONLESS、PENALTY、EXPONENTIAL_DECAY、ROUGH、LAGRANGE 和 USER_DEFINED。默认值为 FRICTIONLESS。

*directionality*

 SymbolicConstant，指定摩擦的方向性。可能的值为 ISOTROPIC 和 ANISOTROPIC。默认值为 ISOTROPIC。

*slipRateDependency*

布尔值，指定数据是否依赖于滑移率。默认值为 OFF。

*pressureDependency*

布尔值，指定数据是否依赖于接触压力。默认值为 OFF。

*temperatureDependency*

布尔值，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

整数，指定场变量的数量。默认值为 0。

*exponentialDecayDefinition*

 SymbolicConstant，指定指数衰减定义。可能的值为 COEFFICIENTS 和 TEST_DATA。默认值为 COEFFICIENTS。

*shearStressLimit*

 `None` 或浮点数，指定剪切应力极限。如果 *shearStressLimit*=`None`，则没有上限。默认值为 `None`。

*maximumElasticSlip*

 SymbolicConstant，指定最大弹性滑移将是什么。可能的值为 FRACTION 和 ABSOLUTE_DISTANCE。默认值为 FRACTION。

*fraction*

浮点数，指定特征表面尺寸的分数。默认值为 0.0。

*absoluteDistance*

浮点数，指定绝对距离。默认值为 0.0。

*elasticSlipStiffness*

 `None` 或浮点数，指定弹性滑移刚度。如果 *elasticSlipStiffness*=`None`，则没有上限。默认值为 `None`。

*nStateDependentVars*

整数，指定状态相关变量的数量。默认值为 0。

*useProperties*

布尔值，指定是否使用属性值。默认值为 OFF。

*table*

浮点数元组的元组，指定切向行为。表格数据中的项目在下面描述。

### 25.25.4 对应的分析关键字

| [*FRICTION](../key/key-link.md#usb-kws-hfriction) |
| --- |
| [*CHANGE FRICTION](../key/key-link.md#usb-kws-hchangefriction) |



