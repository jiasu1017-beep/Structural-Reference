# 29.70 MohrCoulombPlasticity 对象

MohrCoulombPlasticity 对象指定扩展的摩尔-库仑塑性模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].mohrCoulombPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].mohrCoulombPlasticity
```

### 29.70.1 MohrCoulombPlasticity(...)

此方法创建 MohrCoulombPlasticity 对象。

**路径**

```
mdb.models[*name*].materials[*name*].MohrCoulombPlasticity
session.odbs[*name*].materials[*name*].MohrCoulombPlasticity
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*deviatoricEccentricity*

`None` 或 Float，指定偏平面中的流动势偏心率，![](../graphics/ker_eqn00289.gif)；1/2 ≤ *deviatoricEccentricity* ≤ 1.0。如果 *deviatoricEccentricity*=`None`，Abaqus 使用指定的摩尔-库仑摩擦角计算值。默认值为 `None`。

*meridionalEccentricity*

Float，指定子午平面中的流动势偏心率，![](../graphics/ker_eqn00062.gif)。默认值为 0.1。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

*useTensionCutoff*

Boolean，指定是否需要张力截止规范。默认值为 OFF。

**表格数据**

表格数据指定以下内容：
- 高围压下 ![](../graphics/ker_eqn00092.gif)-![](../graphics/ker_eqn00292.gif) 平面中的摩擦角（以度为单位），![](../graphics/ker_eqn00291.gif)。
- 高围压下 ![](../graphics/ker_eqn00092.gif)-![](../graphics/ker_eqn00293.gif) 平面中的膨胀角，![](../graphics/ker_eqn00132.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

MohrCoulombPlasticity 对象。

**异常**

RangeError。

### 29.70.2 setValues(...)

此方法修改 MohrCoulombPlasticity 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [MohrCoulombPlasticity](pt01ch29pyo70.md#ker-mohrcoulombplasticity-mohrcoulombplasticity-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.70.3 成员

MohrCoulombPlasticity 对象的成员与 [MohrCoulombPlasticity](pt01ch29pyo70.md#ker-mohrcoulombplasticity-mohrcoulombplasticity-pyc) 方法的参数具有相同的名称和描述。

此外，MohrCoulombPlasticity 对象可以具有以下成员：

*mohrCoulombHardening*

[MohrCoulombHardening](pt01ch29pyo69.md) 对象。

*tensionCutOff*

[TensionCutOff](pt01ch29pyo97.md) 对象。

### 29.70.4 对应的分析关键字

| [*MOHR COULOMB](../key/key-link.md#usb-kws-mmohrcoulomb) |
| --- |
