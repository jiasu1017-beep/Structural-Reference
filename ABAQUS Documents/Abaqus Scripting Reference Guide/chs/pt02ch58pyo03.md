# 58.3 ConnectorDamage 对象







ConnectorDamage 对象为一个或多个连接器相对运动分量定义损伤行为。

ConnectorDamage 对象派生自 [ConnectorBehaviorOption](pt02ch58pyo01.md) 对象。

**访问**

```
sectionApi.sections()[*name*].behaviorOptions(*i*)
```

### 58.3.1 ConnectorDamage(...)

此方法为 [ConnectorSection](pt02ch63pyo08.md) 对象创建连接器损伤行为选项。

**路径**

```
sectionApi.sections()[*name*].ConnectorDamage
```

**原型**

```
odb_ConnectorDamage&
ConnectorDamage(const odb_String& coupling,
  const odb_String& criterion,
  bool initiationTemperature,
  const odb_String& initiationPotentialOperator,
  double initiationPotentialExponent,
  int initiationDependencies,
  bool evolution,
  const odb_String& evolutionType,
  const odb_String& softening,
  bool useAffected,
  const odb_String& degradation,
  bool evolutionTemperature,
  int evolutionDependencies,
  const odb_String& evolutionPotentialOperator,
  double evolutionPotentialExponent,
  const odb_SequenceConnectorPotential& initiationPotentials,
  const odb_SequenceConnectorPotential& evolutionPotentials,
  const odb_SequenceSequenceDouble& initiationTable,
  const odb_SequenceSequenceDouble& evolutionTable,
  const odb_SequenceInt& affectedComponents,
  const odb_SequenceInt& components);
```

**必需参数**

None。

**可选参数**

*coupling*

一个 odb_String，指定行为是否耦合。可能的值为 "UNCOUPLED" 和 "COUPLED"。默认值为 "UNCOUPLED"。

*criterion*

一个 odb_String，指定损伤起始准则。可能的值为 "FORCE"、"MOTION" 和 "PLASTIC_MOTION"。默认值为 "FORCE"。

*initiationTemperature*

一个 Boolean，指定起始数据是否依赖于温度。默认值为 false。

*initiationPotentialOperator*

一个 odb_String，指定起始势贡献的贡献运算符。可能的值为 "SUM" 和 "MAXIMUM"。默认值为 "SUM"。

此参数仅在 *coupling*="COUPLED" 且 *criterion*="FORCE" 或 "MOTION" 时适用。

*initiationPotentialExponent*

一个 Double，指定起始势定义中整体指数的倒数。默认值为 2.0。

此参数仅在 *coupling*="COUPLED"、*initiationPotentialOperator*="SUM" 且 *criterion*="FORCE" 或 "MOTION" 时适用。

*initiationDependencies*

一个 Int，指定起始数据的场变量依赖项数量。默认值为 0。

*evolution*

一个 Boolean，指定是否使用损伤演化数据。默认值为 true。

*evolutionType*

一个 odb_String，指定要指定的损伤演化类型。可能的值为 "MOTION_TYPE" 和 "ENERGY_TYPE"。默认值为 "MOTION_TYPE"。

此参数仅在 *evolution*=true 时适用。

*softening*

一个 odb_String，指定要指定的损伤演化定律。可能的值为 "LINEAR"、"EXPONENTIAL" 和 "TABULAR"。默认值为 "LINEAR"。

此参数仅在 *evolution*=true 且 *evolutionType*="MOTION_TYPE" 时适用。

*useAffected*

一个 Boolean，指定是否指定 *affectedComponents*。如果 *useAffected*=false，则只有 *components* 指定的相对运动分量会经历损伤。默认值为 false。

此参数仅在 *evolution*=true 时适用。

*degradation*

一个 odb_String，指定当定义了多个损伤机制时每个损伤机制的贡献。可能的值为 "MAXIMUM" 和 "MULTIPLICATIVE"。默认值为 "MAXIMUM"。

此参数在 *evolution*=true 时适用。

*evolutionTemperature*

一个 Boolean，指定演化数据是否依赖于温度。默认值为 false。

此参数仅在 *evolution*=true 时适用。

*evolutionDependencies*

一个 Int，指定演化数据的场变量依赖项数量。默认值为 0。

此参数仅在 *evolution*=true 时适用。

*evolutionPotentialOperator*

一个 odb_String，指定演化势贡献的贡献运算符。可能的值为 "SUM" 和 "MAXIMUM"。默认值为 "SUM"。

此参数仅在 *coupling*="COUPLED"、*evolution*=true、*evolutionType*="MOTION_TYPE" 且 *criterion*="FORCE" 或 "MOTION" 时适用。

*evolutionPotentialExponent*

一个 Double，指定演化势定义中整体指数的倒数。默认值为 2.0。

此参数仅在 *coupling*="COUPLED"、*evolution*=true、*evolutionPotentialOperator*="SUM"、*evolutionType*="MOTION" 且 *criterion*="FORCE" 或 "MOTION" 时适用。

*initiationPotentials*

一个 [ConnectorPotential](pt02ch58pyo11.md) 对象序列，指定每个起始势贡献的一个 [ConnectorPotential](pt02ch58pyo11.md) 对象。此成员仅在 *coupling*="COUPLED" 且 *criterion*="FORCE" 或 "MOTION" 时可以指定。

*evolutionPotentials*

一个 [ConnectorPotential](pt02ch58pyo11.md) 对象序列，指定每个演化势贡献的一个 [ConnectorPotential](pt02ch58pyo11.md) 对象）。此成员仅在 *coupling*="COUPLED"、*evolution*=true、*evolutionType*="MOTION" 且 *criterion*="FORCE" 或 "MOTION" 时可以指定。

*initiationTable*

一个 odb_SequenceSequenceDouble，指定起始属性。默认值为空序列。

*initiationTable* 数据中的项目在下面描述。

*evolutionTable*

一个 odb_SequenceSequenceDouble，指定演化属性。默认值为空序列。

*evolutionTable* 数据中的项目在下面描述。此参数仅在 *evolution*=true 时适用。

*affectedComponents*

一个 odb_SequenceInt，指定将损伤的相对运动分量。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *components* ![](../graphics/ker_eqn00013.gif) 6。仅能指定可用分量。此参数仅在 *evolution*=true 且 *useAffected*=true 时适用。默认值为空序列。

*components*

一个 odb_SequenceInt，指定定义行为的相对运动分量。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *components* ![](../graphics/ker_eqn00013.gif) 6。仅能指定可用分量。此参数仅在 *coupling*="UNCOUPLED" 时可以指定。默认值为空序列。

**表数据**

*initiationTable* 的表数据：

如果 *criterion*=FORCE，则表数据的每个序列指定以下内容：
- 下限（压缩）限制力或力矩。使用 -1.0E+36 表示未指定的下限。
- 上限（拉伸）限制力或力矩。使用 1.0E+36 表示未指定的上限。必须指定下限或上限（至少一个）。
- 如果数据依赖于温度，则为温度。
- 如果数据依赖于场变量，则为第一个场变量的值。
- 第二个场变量的值。
- 依此类推。

如果 *criterion*=MOTION，则表数据的每个序列指定以下内容：
- 下限（压缩）限制连接器结构相对位移或旋转。使用 -1.0E+36 表示未指定的下限。
- 上限（拉伸）限制连接器结构相对位移或旋转。使用 1.0E+36 表示未指定的上限。必须指定下限或上限（至少一个）。
- 如果数据依赖于温度，则为温度。
- 如果数据依赖于场变量，则为第一个场变量的值。
- 第二个场变量的值。
- 依此类推。

如果 *criterion*=PLASTIC_MOTION，则表数据的每个序列指定以下内容：
- 将损伤的相对等效塑性位移/旋转。
- 模式混合比（仅在 *coupling*=COUPLED 时）。
- 相对等效塑性位移/旋转速率。
- 如果数据依赖于温度，则为温度。
- 如果数据依赖于场变量，则为第一个场变量的值。
- 第二个场变量的值。
- 依此类推。

*evolutionTable* 的表数据：

如果 *evolutionType*=MOTION 且 *softening*=LINEAR，则表数据的每个序列指定以下内容：
- 如果 *criterion*=PLASTIC_MOTION，则为最终失效时的失效后相对等效塑性运动。否则，为最终失效时的失效后结构相对运动（位移/旋转）。
- 模式混合比（仅在 *coupling*=COUPLED 且 *criterion*=PLASTIC_MOTION 时）。
- 如果数据依赖于温度，则为温度。
- 如果数据依赖于场变量，则为第一个场变量的值。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=MOTION 且 *softening*=EXPONENTIAL，则表数据的每个序列指定以下内容：
- 如果 *criterion*=PLASTIC_MOTION，则为最终失效时的失效后相对等效塑性运动。否则，为最终失效时的失效后结构相对运动（位移/旋转）。
- 指数律参数。
- 模式混合比（仅在 *coupling*=COUPLED 且 *criterion*=PLASTIC_MOTION 时）。
- 如果数据依赖于温度，则为温度。
- 如果数据依赖于场变量，则为第一个场变量的值。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=MOTION 且 *softening*=TABULAR，则表数据的每个序列指定以下内容：
- 损伤变量（不能小于 0 或大于 1）。
- 如果 *criterion*=PLASTIC_MOTION，则为失效后相对等效塑性运动。否则，为失效后结构相对运动（位移/旋转）。
- 模式混合比（仅在 *coupling*=COUPLED 且 *criterion*=PLASTIC_MOTION 时）。
- 如果数据依赖于温度，则为温度。
- 如果数据依赖于场变量，则为第一个场变量的值。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=ENERGY，则表数据的每个序列指定以下内容：
- 最终失效时损伤消耗的总能量。
- 模式混合比（仅在 *coupling*=COUPLED 且 *criterion*=PLASTIC_MOTION 时）。
- 如果数据依赖于温度，则为温度。
- 如果数据依赖于场变量，则为第一个场变量的值。
- 第二个场变量的值。
- 依此类推。

**返回值**

ConnectorDamage 对象。

**异常**

ValueError 和 TextError。

### 58.3.2 setValues(...)

此方法修改 ConnectorDamage 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [ConnectorDamage](pt02ch58pyo03.md#ker-connectordamage-connectordamage-cpp) 方法的参数相同。

**返回值**

None

**异常**

ValueError。

### 58.3.3 成员

ConnectorDamage 对象具有与 [ConnectorDamage](pt02ch58pyo03.md#ker-connectordamage-connectordamage-cpp) 方法的参数具有相同名称和描述的成员。

此外，ConnectorDamage 对象可以具有以下成员：

**原型**

```
odb_ConnectorOptions initiationOptions() const;
odb_ConnectorOptions evolutionOptions() const;
```

*initiationOptions*

一个 [ConnectorOptions](pt02ch58pyo09.md) 对象，指定用于定义损伤起始表的表格选项的 [ConnectorOptions](pt02ch58pyo09.md)。

*evolutionOptions*

一个 [ConnectorOptions](pt02ch58pyo09.md) 对象，指定用于定义损伤演化表的表格选项的 [ConnectorOptions](pt02ch58pyo09.md)。

### 58.3.4 对应的分析关键字

| [*CONNECTOR DAMAGE INITIATION*](../key/key-link.md#usb-kws-mconnectordamageinit), [*CONNECTOR DAMAGE EVOLUTION*](../key/key-link.md#usb-kws-mconnectordamageevol), [*CONNECTOR POTENTIAL*](../key/key-link.md#usb-kws-mconnectorpotential) |
| --- |

