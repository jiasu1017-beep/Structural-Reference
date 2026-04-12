# 29.21 ConcreteDamagedPlasticity 对象





ConcreteDamagedPlasticity 对象指定混凝土损伤塑性模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity
```

### 29.21.1 ConcreteDamagedPlasticity(...)

此方法创建 ConcreteDamagedPlasticity 对象。

**路径**

```
mdb.models[*name*].materials[*name*].ConcreteDamagedPlasticity
session.odbs[*name*].materials[*name*].ConcreteDamagedPlasticity
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**表格数据**

表格数据指定以下内容：
- 扩容角，![](../graphics/ker_eqn00132.gif)（度），在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面中。
- 流动势偏心率，![](../graphics/ker_eqn00062.gif)。默认值为 0.1。
- ![](../graphics/ker_eqn00133.gif)，初始等双轴压缩屈服应力与初始单轴压缩屈服应力的比值。默认值为 1.16。
- ![](../graphics/ker_eqn00134.gif)，对于任意给定的压力不变量 ![](../graphics/ker_eqn00092.gif)（使最大主应力为负），拉伸子午线上第二应力不变量与压缩子午线上第二应力不变量的比值。默认值为 2/3。
- 粘度参数，![](../graphics/ker_eqn00041.gif)，用于 Abaqus/Standard 分析中混凝土本构方程的粘塑性正则化。此参数在 Abaqus/Explicit 分析中被忽略。默认值为 0.0。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ConcreteDamagedPlasticity 对象。

**异常**

RangeError。

### 29.21.2 setValues(...)

此方法修改 ConcreteDamagedPlasticity 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConcreteDamagedPlasticity](pt01ch29pyo21.md#ker-concretedamagedplasticity-concretedamagedplasticity-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.21.3 成员

ConcreteDamagedPlasticity 对象具有与 [ConcreteDamagedPlasticity](pt01ch29pyo21.md#ker-concretedamagedplasticity-concretedamagedplasticity-pyc) 方法参数同名的成员，描述也相同。

此外，ConcreteDamagedPlasticity 对象可以具有以下成员：

*concreteCompressionHardening*

一个 [ConcreteCompressionHardening](pt01ch29pyo20.md) 对象。

*concreteTensionStiffening*

一个 [ConcreteTensionStiffening](pt01ch29pyo23.md) 对象。

*concreteCompressionDamage*

一个 [ConcreteCompressionDamage](pt01ch29pyo19.md) 对象。

*concreteTensionDamage*

一个 [ConcreteTensionDamage](pt01ch29pyo22.md) 对象。

### 29.21.4 对应的分析关键字

| [*CONCRETE DAMAGED PLASTICITY](../key/key-link.md#usb-kws-mconcretedamagedplast) |
| --- |




