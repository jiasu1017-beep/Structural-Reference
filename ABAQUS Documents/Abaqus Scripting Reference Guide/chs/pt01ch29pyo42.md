# 29.42 DruckerPrager 对象

DruckerPrager 对象指定扩展 Drucker-Prager 塑性模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].druckerPrager
import odbMaterial
session.odbs[*name*].materials[*name*].druckerPrager
```

### 29.42.1 DruckerPrager(...)

此方法创建 DruckerPrager 对象。

**路径**

```
mdb.models[*name*].materials[*name*].DruckerPrager
session.odbs[*name*].materials[*name*].DruckerPrager
```

**必需参数**

*table*

 Float 元组序列，指定下述项目。

**可选参数**

*shearCriterion*

 SymbolicConstant，指定屈服准则。可能的值为 LINEAR、HYPERBOLIC 和 EXPONENTIAL。默认值为 LINEAR。

此参数仅适用于 Abaqus/Standard 分析。仅线性 Drucker-Prager 模型在 Abaqus/Explicit 分析中可用。

*eccentricity*

 Float，指定流动势偏心率，![](../graphics/ker_eqn00062.gif)，一个确定双曲线流动势接近其渐近线速率的小正数。默认值为 0.1。

此参数仅适用于 Abaqus/Standard 分析。

*testData*

 Boolean，指定是否由 Abaqus/Standard 从不同围压水平的三轴试验数据计算指数模型的材料常数。默认值为 OFF。

此参数仅在 *shearCriterion*=EXPONENTIAL 时有效。

*temperatureDependency*

 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

如果 *shearCriterion*=LINEAR（Abaqus/Explicit 分析中唯一允许的选项），表格数据指定以下内容：
- 材料摩擦角，![](../graphics/ker_eqn00095.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) 平面中。以度为单位给出值。
- ![](../graphics/ker_eqn00099.gif)，三轴拉伸流动应力与三轴压缩流动应力之比。![](../graphics/ker_eqn00110.gif)。如果接受默认值 0.0，则假定值为 1.0。
- 膨胀角，![](../graphics/ker_eqn00132.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) 平面中。以度为单位给出值。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *shearCriterion*=HYPERBOLIC，表格数据指定以下内容：
- 高围压下材料摩擦角，![](../graphics/ker_eqn00095.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面中。以度为单位给出值。
- 初始静水拉力强度，![](../graphics/ker_eqn00177.gif)。
- 高围压下膨胀角，![](../graphics/ker_eqn00132.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面中。以度为单位给出值。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *shearCriterion*=EXPONENTIAL，表格数据指定以下内容：
- 高围压下膨胀角，![](../graphics/ker_eqn00132.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面中。以度为单位给出值。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

 DruckerPrager 对象。

**异常**

 RangeError。

### 29.42.2 setValues(...)

此方法修改 DruckerPrager 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [DruckerPrager](pt01ch29pyo42.md#ker-druckerprager-druckerprager-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.42.3 成员

DruckerPrager 对象的成员与 [DruckerPrager](pt01ch29pyo42.md#ker-druckerprager-druckerprager-pyc) 方法的参数具有相同的名称和描述。

此外，DruckerPrager 对象可以具有以下成员：

*druckerPragerCreep*

 [DruckerPragerCreep](pt01ch29pyo43.md) 对象。

*druckerPragerHardening*

 [DruckerPragerHardening](pt01ch29pyo44.md) 对象。

*rateDependent*

 [RateDependent](pt01ch29pyo85.md) 对象。

*triaxialTestData*

 [TriaxialTestData](pt01ch29pyo99.md) 对象。

### 29.42.4 对应的分析关键字

| [*DRUCKER PRAGER](../key/key-link.md#usb-kws-mdruckerprager) |
| --- |
