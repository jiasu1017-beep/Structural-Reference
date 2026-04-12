# 12.5 ConnectorElasticity 对象

ConnectorElasticity 对象为连接器相对运动的一个或多个分量定义弹性行为。

ConnectorElasticity 对象派生自 [ConnectorBehaviorOption](pt01ch12pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]
import odbSection
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]
```

### 12.5.1 ConnectorElasticity(...)

此方法为 [ConnectorSection](pt01ch46pyo08.md) 对象创建连接器弹性行为选项。

**路径**

```
mdb.models[*name*].sections[*name*].ConnectorElasticity
session.odbs[*name*].sections[*name*].ConnectorElasticity
```

**必需参数**

无。

**可选参数**

*behavior*

SymbolicConstant，指定弹性行为是线性、非线性还是刚性。可能的值为 LINEAR、NONLINEAR 和 RIGID。默认值为 LINEAR。

*coupling*

SymbolicConstant，指定弹性行为是否在连接器的相对运动分量之间耦合。如果 *behavior*=LINEAR，则可能的值为 UNCOUPLED 和 COUPLED。如果 *behavior*=NONLINEAR，则可能的值为 UNCOUPLED、COUPLED_POSITION 和 COUPLED_MOTION。可能的值为 UNCOUPLED、COUPLED、COUPLED_POSITION 和 COUPLED_MOTION。默认值为 UNCOUPLED。

此参数在 *behavior*=RIGID 时不适用。

*dependencies*

Int，指定场变量依赖数量。默认值为 0。

此参数在 *behavior*=RIGID 时不适用。

*temperatureDependency*

Boolean，指定行为数据是否依赖于温度。默认值为 OFF。

此参数在 *behavior*=RIGID 时不适用。

*frequencyDependency*

Boolean，指定行为数据是否依赖于频率。此值仅在 *behavior*=LINEAR 且 *coupling*=UNCOUPLED 时适用。默认值为 OFF。

此参数在 *behavior*=RIGID 时不适用。

*table*

Float 的序列的序列，指定弹性属性。表格数据中的项如下所述。此参数在 *behavior*=RIGID 时不适用。默认值为空序列。

*independentComponents*

Int 的序列，指定包含在连接器弹性数据定义中的独立分量列表。此参数仅在 *behavior*=NONLINEAR 且 *coupling*=COUPLED_POSITION 或 COUPLED_MOTION 时适用。如果此参数适用，则必须指定至少一个值。只能指定可用的分量。默认值为空序列。

*components*

Int 的序列，指定定义行为的相对运动分量。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *components* ![](../graphics/ker_eqn00013.gif) 6。只能指定可用的分量。默认值为空序列。

**表格数据**

如果 *behavior*=LINEAR 且 *coupling*=UNCOUPLED，则表格数据的每个序列指定以下内容：
- 弹性刚度（每个力/力矩分量）。
- 频率（周期/时间）（如果数据依赖于频率）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *behavior*=NONLINEAR 且 *coupling*=UNCOUPLED，则表格数据的每个序列指定以下内容：
- 力或力矩。
- 相对位移或旋转。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *behavior*=LINEAR 且 *coupling*=COUPLED，则表格数据为指定分量指定弹性刚度矩阵的对称部分，然后是任何温度数据，最后是任何场数据。例如，如果指定了分量 2、3 和 5，则命令的表格部分如下：
```
table=( (![](../graphics/ker_eqn00031.gif), ![](../graphics/ker_eqn00032.gif), ![](../graphics/ker_eqn00033.gif), ![](../graphics/ker_eqn00034.gif), ![](../graphics/ker_eqn00035.gif), ![](../graphics/ker_eqn00036.gif),),
)
```
然后应将以下项指定为逗号分隔的数据：
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *behavior*=NONLINEAR 且 *coupling*=COUPLED_POSITION 或 COUPLED_MOTION，则表格数据的每个序列指定以下内容：
- *components* 列表中方向的力或力矩。
- 如果 *coupling*=COUPLED_POSITION，则为第一个 *independentComponents* 方向的相对位置或角度。如果 *coupling*=COUPLED_MOTION，则为第一个 *independentComponents* 方向的相对位移或旋转。
- 如果 *coupling*=COUPLED_POSITION，则为第二个 *independentComponents* 方向的相对位置或角度。如果 *coupling*=COUPLED_MOTION，则为第二个 *independentComponents* 方向的相对位移或旋转。
- 依此类推，直到第 N 个 *independentComponents* 方向。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

ConnectorElasticity 对象。

**异常**

ValueError 和 TextError。

### 12.5.2 setValues(...)

此方法修改 ConnectorElasticity 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConnectorElasticity](pt01ch12pyo05.md#ker-connectorelasticity-connectorelasticity-pyc) 方法的参数相同。

**返回值**

无。

**异常**

ValueError。

### 12.5.3 成员

ConnectorElasticity 对象的成员与 [ConnectorElasticity](pt01ch12pyo05.md#ker-connectorelasticity-connectorelasticity-pyc) 方法的参数具有相同的名称和描述。

此外，ConnectorElasticity 对象可以具有以下成员：

*options*

[ConnectorOptions](pt01ch12pyo09.md) 对象，指定用于定义此 [ConnectorBehaviorOption](pt01ch12pyo01.md) 的表格选项的 [ConnectorOptions](pt01ch12pyo09.md)。

### 12.5.4 对应的分析关键字

| [*CONNECTOR ELASTICITY](../key/key-link.md#usb-kws-mconnectorelasticity) |
| --- |
