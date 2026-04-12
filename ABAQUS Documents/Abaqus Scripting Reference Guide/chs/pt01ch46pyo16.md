# 46.16 MembraneSection 对象

MembraneSection 对象定义薄膜截面的属性。

MembraneSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.16.1 MembraneSection(...)

此方法创建 MembraneSection 对象。

**Path**

```
mdb.models[*name*].MembraneSection
session.odbs[*name*].MembraneSection
```

**必需参数**

*name*

String，指定存储库键。

*material*

String，指定材料名称。

**可选参数**

*thickness*

Float，指定截面的厚度。可能的值为 *thickness* ![](../graphics/ker_eqn00060.gif) 0.0。默认值为 1.0。

*thicknessType*

SymbolicConstant，指定用于定义单元厚度的分布。可选值为 UNIFORM、ANALYTICAL_FIELD 和 DISCRETE_FIELD。默认值为 UNIFORM。

*poissonDefinition*

SymbolicConstant，指定是否使用泊松比的默认值。可选值为：
- DEFAULT，指定在 Abaqus/Standard 分析中泊松比的默认值为 0.5，在 Abaqus/Explicit 分析中从材料定义获取。
- VALUE，指定分析中使用的泊松比是 *poisson* 提供的值。

默认值为 DEFAULT。

*poisson*

Float，指定截面泊松比。可能的值为 1.0 ![](../graphics/ker_eqn00013.gif) *poisson* ![](../graphics/ker_eqn00013.gif) 0.5。此参数仅在 *poissonDefinition*=VALUE 时有效。默认值为 0.5。

*thicknessField*

String，指定 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称，用于定义壳单元的厚度。*thicknessField* 参数仅在 *thicknessType*=ANALYTICAL_FIELD 或 *thicknessType*=DISCRETE_FIELD 时适用。默认值为空字符串。

**返回值**

MembraneSection 对象。

**异常**

RangeError 和 InvalidNameError。

### 46.16.2 setValues(...)

此方法修改 MembraneSection 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [MembraneSection](pt01ch46pyo16.md#ker-membranesection-membranesection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 46.16.3 成员

MembraneSection 对象的成员与 [MembraneSection](pt01ch46pyo16.md#ker-membranesection-membranesection-pyc) 方法的参数具有相同的名称和描述。

此外，MembraneSection 对象可以具有以下成员：

*rebarLayers*

[RebarLayers](pt01ch46pyo19.md) 对象，指定增强属性。

### 46.16.4 对应分析关键字

| [*MEMBRANE SECTION*](../key/key-link.md#usb-kws-mmembranesection) |
| --- |
