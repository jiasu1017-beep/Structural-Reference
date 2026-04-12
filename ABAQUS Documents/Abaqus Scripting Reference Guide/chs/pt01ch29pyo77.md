# 29.77 Plastic 对象

Plastic 对象指定金属塑性模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].plastic
import odbMaterial
session.odbs[*name*].materials[*name*].plastic
```

### 29.77.1 Plastic(...)

此方法创建 Plastic 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Plastic
session.odbs[*name*].materials[*name*].Plastic
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*hardening*

SymbolicConstant，指定硬化类型。可能的值为 ISOTROPIC、KINEMATIC、COMBINED、JOHNSON_COOK 和 USER。默认值为 ISOTROPIC。

*rate*

Boolean，指定数据是否依赖于速率。默认值为 OFF。

*dataType*

SymbolicConstant，指定组合硬化类型。此参数仅在 *hardening*=COMBINED 时有效。可能的值为 HALF_CYCLE、PARAMETERS 和 STABILIZED。默认值为 HALF_CYCLE。

*strainRangeDependency*

Boolean，指定数据是否依赖于应变范围。此参数仅在 *hardening*=COMBINED 且 *dataType*=STABILIZED 时有效。默认值为 OFF。

*numBackstresses*

Int，指定背应力数量。此参数仅在 *hardening*=COMBINED 时有效。默认值为 1。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

如果 *hardening*=ISOTROPIC，或如果 *hardening*=COMBINED 且 *dataType*=HALF_CYCLE，表格数据指定以下内容：
- 屈服应力。
- 塑性应变。
- 等效塑性应变率，![](../graphics/ker_eqn00337.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *hardening*=COMBINED 且 *dataType*=STABILIZED，表格数据指定以下内容：
- 屈服应力。
- 塑性应变。
- 应变范围（如果数据依赖于应变范围）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *hardening*=COMBINED 且 *dataType*=PARAMETERS，表格数据指定以下内容：
- 零塑性应变时的屈服应力。
- 第一个运动硬化参数，![](../graphics/ker_eqn00338.gif)。
- 第一个运动硬化参数，![](../graphics/ker_eqn00339.gif)。
- 如果适用，第二个运动硬化参数，![](../graphics/ker_eqn00340.gif)。
- 如果适用，第二个运动硬化参数，![](../graphics/ker_eqn00341.gif)。
- 以此类推。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *hardening*=KINEMATIC，表格数据指定以下内容：
- 屈服应力。
- 塑性应变。
- 温度（如果数据依赖于温度）。

如果 *hardening*=JOHNSON_COOK，表格数据指定以下内容：
- A。
- B。
- n。
- m。
- 熔化温度。
- 转变温度。

如果 *hardening*=USER，表格数据指定以下内容：
- 硬化属性。

**返回值**

Plastic 对象。

**异常**

RangeError。

### 29.77.2 setValues(...)

此方法修改 Plastic 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Plastic](pt01ch29pyo77.md#ker-plastic-plastic-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.77.3 成员

Plastic 对象的成员与 [Plastic](pt01ch29pyo77.md#ker-plastic-plastic-pyc) 方法的参数具有相同的名称和描述。

此外，Plastic 对象可以具有以下成员：

*rateDependent*

[RateDependent](pt01ch29pyo85.md) 对象。

*potential*

[Potential](pt01ch29pyo83.md) 对象。

*cyclicHardening*

[CyclicHardening](pt01ch29pyo30.md) 对象。

*ornl*

[Ornl](pt01ch29pyo73.md) 对象。

*cycledPlastic*

[CycledPlastic](pt01ch29pyo29.md) 对象。

*annealTemperature*

[AnnealTemperature](pt01ch29pyo03.md) 对象。

### 29.77.4 对应的分析关键字

| [*PLASTIC](../key/key-link.md#usb-kws-mplastic) |
| --- |
