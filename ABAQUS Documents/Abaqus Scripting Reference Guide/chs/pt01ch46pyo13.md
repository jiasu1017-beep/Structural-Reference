# 46.13 HomogeneousShellSection 对象

HomogeneousShellSection 对象定义壳截面的属性。

HomogeneousShellSection 对象派生自 [GeometryShellSection](pt01ch46pyo12.md) 对象。

**访问**

```
import section
mdb.models[*name*].parts[*name*].compositeLayups[*i*].section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.13.1 HomogeneousShellSection(...)

此方法创建 HomogeneousShellSection 对象。

**Path**

```
mdb.models[*name*].parts[*name*].compositeLayups[*i*].HomogeneousShellSection
mdb.models[*name*].HomogeneousShellSection
session.odbs[*name*].HomogeneousShellSection
```

**必需参数**

*name*

String，指定存储库键。

*material*

String，指定截面材料的名称。

**可选参数**

*thickness*

Float，指定截面的厚度。*thickness* 参数仅在 *thicknessType*=UNIFORM 时适用。默认值为 0.0。

*numIntPts*

Int，指定通过截面使用的积分点数量。可能的值为 *numIntPts* ![](../graphics/ker_eqn00060.gif) 0。默认值为 5。

要使用分析产品的默认设置，如果 *integrationRule*=SIMPSON，则将 *numIntPts* 设置为 5；如果 *integrationRule*=GAUSS，则将 *numIntPts* 设置为 7。

*thicknessType*

SymbolicConstant，指定用于定义单元厚度的分布。可选值为 UNIFORM、ANALYTICAL_FIELD、DISCRETE_FIELD、NODAL_ANALYTICAL_FIELD 和 NODAL_DISCRETE_FIELD。默认值为 UNIFORM。

*preIntegrate*

Boolean，指定壳截面属性是由用户在分析前指定（ON）还是在分析期间积分（OFF）。默认值为 OFF。

*poissonDefinition*

SymbolicConstant，指定是否使用泊松比的默认值。可选值为：
- DEFAULT，指定在 Abaqus/Standard 分析中泊松比的默认值为 0.5，在 Abaqus/Explicit 分析中从材料定义获取。
- VALUE，指定分析中使用的泊松比是 *poisson* 提供的值。

默认值为 DEFAULT。

*poisson*

Float，指定泊松比。可能的值为 1.0 ![](../graphics/ker_eqn00013.gif) *poisson* ![](../graphics/ker_eqn00013.gif) 0.5。此参数仅在 *poissonDefinition*=VALUE 时有效。默认值为 0.5。

*integrationRule*

SymbolicConstant，指定壳截面积分规则。可选值为 SIMPSON 和 GAUSS。默认值为 SIMPSON。

*temperature*

SymbolicConstant，指定通过截面厚度输入温度和场变量的模式。可选值为 GRADIENT 和 POINTWISE。默认值为 GRADIENT。

*idealization*

SymbolicConstant，指定用于截面计算的机械理想化。此成员仅在 *preIntegrate* 设置为 ON 时适用。可选值为 NO_IDEALIZATION、SMEAR_ALL_LAYERS、MEMBRANE 和 BENDING。默认值为 NO_IDEALIZATION。

*nTemp*

`None` 或 Int，指定要输入的温度点数量。此参数仅在 *temperature*=POINTWISE 时有效。默认值为 `None`。

*thicknessModulus*

`None` 或 Float，指定有效厚度模量。此参数仅与连续壳相关，必须与 *poisson* 参数一起使用。默认值为 `None`。

*useDensity*

Boolean，指定是否使用 *density* 的值。默认值为 OFF。

*density*

Float，指定要应用于此截面的密度值。默认值为 0.0。

*thicknessField*

String，指定 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称，用于定义壳单元的厚度。*thicknessField* 参数仅在 *thicknessType*=ANALYTICAL_FIELD 或 *thicknessType*=DISCRETE_FIELD 时适用。默认值为空字符串。

*nodalThicknessField*

String，指定 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称，用于定义每个节点处壳单元的厚度。*nodalThicknessField* 参数仅在 *thicknessType*=NODAL_ANALYTICAL_FIELD 或 *thicknessType*=NODAL_DISCRETE_FIELD 时适用。默认值为空字符串。

**返回值**

HomogeneousShellSection 对象。

**异常**

无。

### 46.13.2 setValues(...)

此方法修改 HomogeneousShellSection 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [HomogeneousShellSection](pt01ch46pyo13.md#ker-homogeneousshellsection-homogeneousshellsection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 46.13.3 成员

HomogeneousShellSection 对象的成员与 [HomogeneousShellSection](pt01ch46pyo13.md#ker-homogeneousshellsection-homogeneousshellsection-pyc) 方法的参数具有相同的名称和描述。

此外，HomogeneousShellSection 对象可以具有以下成员：

*rebarLayers*

[RebarLayers](pt01ch46pyo19.md) 对象，指定增强属性。

*transverseShear*

[TransverseShearShell](pt01ch46pyo25.md) 对象，指定横向剪切刚度属性。

### 46.13.4 对应分析关键字

| [*SHELL SECTION*](../key/key-link.md#usb-kws-mshellsection) |
| --- |
| [*SHELL GENERAL SECTION*](../key/key-link.md#usb-kws-mshellgensect) |
