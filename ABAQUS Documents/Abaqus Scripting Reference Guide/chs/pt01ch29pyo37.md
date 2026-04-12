# 29.37 Density 对象





Density 对象指定材料密度。

**访问**

```
import material
mdb.models[*name*].materials[*name*].density
import odbMaterial
session.odbs[*name*].materials[*name*].density
```

### 29.37.1 Density(...)

此方法创建 Density 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Density
session.odbs[*name*].materials[*name*].Density
```

**必需参数**

*table*

一个 Float 元组序列，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖项的数量。默认值为 0。

*distributionType*

一个 SymbolicConstant，指定密度如何空间分布。可能的值为 UNIFORM、ANALYTICAL_FIELD 和 DISCRETE_FIELD。默认值为 UNIFORM。

*fieldName*

一个 String，指定与此材料选项关联的 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称。*fieldName* 参数仅在 *distributionType*=ANALYTICAL_FIELD 或 *distributionType*=DISCRETE_FIELD 时适用。默认值为空字符串。

**表格数据**

- 质量密度。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Density 对象。

**异常**

RangeError。

### 29.37.2 setValues(...)

此方法修改 Density 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Density](pt01ch29pyo37.md#ker-density-density-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.37.3 成员

Density 对象具有与 [Density](pt01ch29pyo37.md#ker-density-density-pyc) 方法参数同名的成员，描述也相同。

### 29.37.4 对应的分析关键字

| [*DENSITY](../key/key-link.md#usb-kws-mdensity) |
| --- |




