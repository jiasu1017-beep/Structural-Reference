# 29.85 RateDependent 对象

RateDependent 对象定义率相关粘塑性模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].crushableFoam.rateDependent
mdb.models[*name*].materials[*name*].druckerPrager.rateDependent
mdb.models[*name*].materials[*name*].plastic.rateDependent
import odbMaterial
session.odbs[*name*].materials[*name*].crushableFoam.rateDependent
session.odbs[*name*].materials[*name*].druckerPrager.rateDependent
session.odbs[*name*].materials[*name*].plastic.rateDependent
```

### 29.85.1 RateDependent(...)

此方法创建 RateDependent 对象。

**路径**

```
mdb.models[*name*].materials[*name*].crushableFoam.RateDependent
mdb.models[*name*].materials[*name*].druckerPrager.RateDependent
mdb.models[*name*].materials[*name*].plastic.RateDependent
session.odbs[*name*].materials[*name*].crushableFoam.RateDependent
session.odbs[*name*].materials[*name*].druckerPrager.RateDependent
session.odbs[*name*].materials[*name*].plastic.RateDependent
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*type*

SymbolicConstant，指定率相关数据的类型。可能的值为 POWER_LAW、YIELD_RATIO 和 JOHNSON_COOK。默认值为 POWER_LAW。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

如果 *type*=POWER_LAW，表格数据指定以下内容：
- ![](../graphics/ker_eqn00172.gif)。
- ![](../graphics/ker_eqn00088.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=YIELD_RATIO，表格数据指定以下内容：
- 屈服应力比，![](../graphics/ker_eqn00357.gif)。
- 等效塑性应变率，![](../graphics/ker_eqn00337.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=JOHNSON_COOK，表格数据指定以下内容：
- ![](../graphics/ker_eqn00039.gif)。
- ![](../graphics/ker_eqn00358.gif)。

**返回值**

RateDependent 对象。

**异常**

RangeError。

### 29.85.2 setValues(...)

此方法修改 RateDependent 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [RateDependent](pt01ch29pyo85.md#ker-ratedependent-ratedependent-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.85.3 成员

RateDependent 对象的成员与 [RateDependent](pt01ch29pyo85.md#ker-ratedependent-ratedependent-pyc) 方法的参数具有相同的名称和描述。

### 29.85.4 对应的分析关键字

| [*RATE DEPENDENT](../key/key-link.md#usb-kws-mratedependent) |
| --- |
