# 46.11 GeneralStiffnessSection 对象

GeneralStiffnessSection 对象通过刚度矩阵定义壳截面的属性。

GeneralStiffnessSection 对象派生自 [ShellSection](pt01ch46pyo21.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.11.1 GeneralStiffnessSection(...)

此方法创建 GeneralStiffnessSection 对象。

**Path**

```
mdb.models[*name*].GeneralStiffnessSection
session.odbs[*name*].GeneralStiffnessSection
```

**必需参数**

*name*

String，指定存储库键。

*stiffnessMatrix*

Float 序列，指定截面刚度矩阵，顺序为 D11、D12、D22、D13、D23、D33、...、D66。必须给出 21 个条目。

**可选参数**

*referenceTemperature*

`None` 或 Float，指定热膨胀的参考温度。默认值为 `None`。

*applyThermalStress*

Boolean，指定截面刚度是否随热应力变化。默认值为 OFF。

*temperatureDependency*

Boolean，指定数据是否依赖温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

*poissonDefinition*

SymbolicConstant，指定是否使用泊松比的默认值。可选值为：
- DEFAULT，指定在 Abaqus/Standard 分析中泊松比的默认值为 0.5，在 Abaqus/Explicit 分析中从材料定义获取。
- VALUE，指定分析中使用的泊松比是 *poisson* 提供的值。

默认值为 DEFAULT。

*poisson*

Float，指定泊松比。可能的值为 1.0 ![](../graphics/ker_eqn00013.gif) *poisson* ![](../graphics/ker_eqn00013.gif) 0.5。此参数仅在 *poissonDefinition*=VALUE 时有效。默认值为 0.5。

*useDensity*

Boolean，指定是否使用 *density* 的值。默认值为 OFF。

*density*

Float，指定要应用于此截面的密度值。默认值为 0.0。

*thermalStresses*

Float 序列，指定单位温升引起的广义应力值。如果 *applyThermalStress* 设置为 True，则必须给出 6 个条目。默认值为 ("")。

*scalingData*

Float 序列的序列，指定给定温度和/或场数据的缩放因子。每一行应包含 (Y, alpha, T, F1,...,Fn)。默认值为空序列。

**返回值**

GeneralStiffnessSection 对象。

**异常**

无。

### 46.11.2 setValues(...)

此方法修改 GeneralStiffnessSection 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [GeneralStiffnessSection](pt01ch46pyo11.md#ker-generalstiffnesssection-generalstiffnesssection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 46.11.3 成员

GeneralStiffnessSection 对象的成员与 [GeneralStiffnessSection](pt01ch46pyo11.md#ker-generalstiffnesssection-generalstiffnesssection-pyc) 方法的参数具有相同的名称和描述。

此外，GeneralStiffnessSection 对象可以具有以下成员：

*rebarLayers*

[RebarLayers](pt01ch46pyo19.md) 对象，指定增强属性。

*transverseShear*

[TransverseShearShell](pt01ch46pyo25.md) 对象，指定横向剪切刚度属性。

### 46.11.4 对应分析关键字

| [*SHELL GENERAL SECTION*](../key/key-link.md#usb-kws-mshellgensect) |
| --- |
