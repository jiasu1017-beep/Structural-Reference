# 12.3 ConnectorDamage 对象

ConnectorDamage 对象为连接器相对运动的一个或多个分量定义损伤行为。

ConnectorDamage 对象派生自 [ConnectorBehaviorOption](pt01ch12pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]
import odbSection
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]
```

### 12.3.1 ConnectorDamage(...)

此方法为 [ConnectorSection](pt01ch46pyo08.md) 对象创建连接器损伤行为选项。

**路径**

```
mdb.models[*name*].sections[*name*].ConnectorDamage
session.odbs[*name*].sections[*name*].ConnectorDamage
```

**必需参数**

无。

**可选参数**

*coupling*

SymbolicConstant，指定行为是否耦合。可能的值为 UNCOUPLED 和 COUPLED。默认值为 UNCOUPLED。

*criterion*

SymbolicConstant，指定要使用的损伤起始准则。可能的值为 FORCE、MOTION 和 PLASTIC_MOTION。默认值为 FORCE。

*initiationTemperature*

Boolean，指定起始数据是否依赖于温度。默认值为 OFF。

*initiationPotentialOperator*

SymbolicConstant，指定起始势贡献的运算符。可能的值为 SUM 和 MAXIMUM。默认值为 SUM。

仅在 *coupling*=COUPLED 且 *criterion*=FORCE 或 MOTION 时适用。

*initiationPotentialExponent*

Float，指定起始势定义中总体指数的倒数。默认值为 2.0。

此参数仅在 *coupling*=COUPLED、*initiationPotentialOperator*=SUM 且 *criterion*=FORCE 或 MOTION 时适用。

*initiationDependencies*

Int，指定起始数据的场变量依赖数量。默认值为 0。

*evolution*

Boolean，指定是否使用损伤演化数据。默认值为 ON。

*evolutionType*

SymbolicConstant，指定要指定的损伤演化类型。可能的值为 MOTION_TYPE 和 ENERGY_TYPE。默认值为 MOTION_TYPE。

此参数仅在 *evolution*=ON 时适用。

*softening*

SymbolicConstant，指定要指定的损伤演化定律。可能的值为 LINEAR、EXPONENTIAL 和 TABULAR。默认值为 LINEAR。

此参数仅在 *evolution*=ON 且 *evolutionType*=MOTION_TYPE 时适用。

*useAffected*

Boolean，指定是否要指定 *affectedComponents*。如果 *useAffected*=OFF，则只有 *components* 指定的相对运动分量会发生损伤。默认值为 OFF。

此参数仅在 *evolution*=ON 时适用。

*degradation*

SymbolicConstant，指定当定义多个损伤机制时每个损伤机制的贡献。可能的值为 MAXIMUM 和 MULTIPLICATIVE。默认值为 MAXIMUM。

此参数在 *evolution*=ON 时适用。

*evolutionTemperature*

Boolean，指定演化数据是否依赖于温度。默认值为 OFF。

此参数仅在 *evolution*=ON 时适用。

*evolutionDependencies*

Int，指定演化数据的场变量依赖数量。默认值为 0。

此参数仅在 *evolution*=ON 时适用。

*evolutionPotentialOperator*

SymbolicConstant，指定演化势贡献的运算符。可能的值为 SUM 和 MAXIMUM。默认值为 SUM。

此参数仅在 *coupling*=COUPLED、*evolution*=ON、*evolutionType*=MOTION_TYPE 且 *criterion*=FORCE 或 MOTION 时适用。

*evolutionPotentialExponent*

Float，指定演化势定义中总体指数的倒数。默认值为 2.0。

此参数仅在 *coupling*=COUPLED、*evolution*=ON、*evolutionPotentialOperator*=SUM、*evolutionType*=MOTION 且 *criterion*=FORCE 或 MOTION 时适用。

*initiationPotentials*

[ConnectorPotentialArray](pt01ch12pyo11.md) 对象，为每个起始势贡献指定一个 [ConnectorPotential](pt01ch12pyo11.md) 对象。此成员仅在 *coupling*=COUPLED 且 *criterion*=FORCE 或 MOTION 时可以指定。

*evolutionPotentials*

[ConnectorPotentialArray](pt01ch12pyo11.md) 对象，为每个演化势贡献指定一个 [ConnectorPotential](pt01ch12pyo11.md) 对象。此成员仅在 *coupling*=COUPLED、*evolution*=ON、*evolutionType*=MOTION 且 *criterion*=FORCE 或 MOTION 时可以指定。

*initiationTable*

Float 的序列的序列，指定起始属性。默认值为空序列。

*initiationTable* 数据中的项如下所述。

*evolutionTable*

Float 的序列的序列，指定演化属性。默认值为空序列。

*evolutionTable* 数据中的项如下所述。此参数仅在 *evolution*=ON 时适用。

*affectedComponents*

Int 的序列，指定将发生损伤的相对运动分量。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *components* ![](../graphics/ker_eqn00013.gif) 6。只能指定可用的分量。此参数仅在 *evolution*=ON 且 *useAffected*=ON 时适用。默认值为空序列。

*components*

Int 的序列，指定定义行为的相对运动分量。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *components* ![](../graphics/ker_eqn00013.gif) 6。只能指定可用的分量。此参数仅在 *coupling*=UNCOUPLED 时可以指定。默认值为空序列。

**表格数据**

*initiationTable* 的表格数据：

如果 *criterion*=FORCE，则表格数据的每个序列指定以下内容：
- 下限（压缩）约束力或力矩。使用 -1.0E+36 表示未指定的下限。
- 上限（拉伸）约束力或力矩。使用 1.0E+36 表示未指定的上限。必须指定下限或上限之一。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *criterion*=MOTION，则表格数据的每个序列指定以下内容：
- 下限（压缩）约束连接器相对位移或旋转。使用 -1.0E+36 表示未指定的下限。
- 上限（拉伸）约束连接器相对位移或旋转。使用 1.0E+36 表示未指定的上限。必须指定下限或上限之一。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *criterion*=PLASTIC_MOTION，则表格数据的每个序列指定以下内容：
- 将发生损伤的相对等效塑性位移/旋转。
- 模式混合比（仅在 *coupling*=COUPLED 时）。
- 相对等效塑性位移/旋转速率。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

*evolutionTable* 的表格数据：

如果 *evolutionType*=MOTION 且 *softening*=LINEAR，则表格数据的每个序列指定以下内容：
- 如果 *criterion*=PLASTIC_MOTION，则为最终失效时的失效后相对塑性运动。否则，为最终失效时的失效后结构相对运动（位移/旋转）。
- 模式混合比（仅在 *coupling*=COUPLED 且 *criterion*=PLASTIC_MOTION 时）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=MOTION 且 *softening*=EXPONENTIAL，则表格数据的每个序列指定以下内容：
- 如果 *criterion*=PLASTIC_MOTION，则为最终失效时的失效后相对塑性运动。否则，为最终失效时的失效后结构相对运动（位移/旋转）。
- 指数律参数。
- 模式混合比（仅在 *coupling*=COUPLED 且 *criterion*=PLASTIC_MOTION 时）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=MOTION 且 *softening*=TABULAR，则表格数据的每个序列指定以下内容：
- 损伤变量（不能小于 0 或大于 1）。
- 如果 *criterion*=PLASTIC_MOTION，则为失效后相对等效塑性运动。否则，为失效后结构相对运动（位移/旋转）。
- 模式混合比（仅在 *coupling*=COUPLED 且 *criterion*=PLASTIC_MOTION 时）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=ENERGY，则表格数据的每个序列指定以下内容：
- 最终失效时损伤消耗的总能量。
- 模式混合比（仅在 *coupling*=COUPLED 且 *criterion*=PLASTIC_MOTION 时）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

ConnectorDamage 对象。

**异常**

ValueError 和 TextError。

### 12.3.2 setValues(...)

此方法修改 ConnectorDamage 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConnectorDamage](pt01ch12pyo03.md#ker-connectordamage-connectordamage-pyc) 方法的参数相同。

**返回值**

无。

**异常**

ValueError。

### 12.3.3 成员

ConnectorDamage 对象的成员与 [ConnectorDamage](pt01ch12pyo03.md#ker-connectordamage-connectordamage-pyc) 方法的参数具有相同的名称和描述。

此外，ConnectorDamage 对象可以具有以下成员：

*initiationOptions*

[ConnectorOptions](pt01ch12pyo09.md) 对象，指定用于定义损伤起始表格选项的 [ConnectorOptions](pt01ch12pyo09.md)。

*evolutionOptions*

[ConnectorOptions](pt01ch12pyo09.md) 对象，指定用于定义损伤演化表格选项的 [ConnectorOptions](pt01ch12pyo09.md)。

### 12.3.4 对应的分析关键字

| [*CONNECTOR DAMAGE INITIATION](../key/key-link.md#usb-kws-mconnectordamageinit), [*CONNECTOR DAMAGE EVOLUTION](../key/key-link.md#usb-kws-mconnectordamageevol), [*CONNECTOR POTENTIAL](../key/key-link.md#usb-kws-mconnectorpotential) |
| --- |
