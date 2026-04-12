# 29.95 SpecificHeat 对象

SpecificHeat 对象指定材料的比热容。

**访问**

```
import material
mdb.models[*name*].materials[*name*].specificHeat
import odbMaterial
session.odbs[*name*].materials[*name*].specificHeat
```

### 29.95.1 SpecificHeat(...)

此方法创建 SpecificHeat 对象。

**路径**

```
mdb.models[*name*].materials[*name*].SpecificHeat
session.odbs[*name*].materials[*name*].SpecificHeat
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*law*

SymbolicConstant，指定比热容行为。可能的值为 CONSTANTVOLUME 和 CONSTANTPRESSURE。默认值为 CONSTANTVOLUME。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

- 单位质量的比热容。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

SpecificHeat 对象。

**异常**

RangeError。

### 29.95.2 setValues(...)

此方法修改 SpecificHeat 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SpecificHeat](pt01ch29pyo95.md#ker-specificheat-specificheat-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.95.3 成员

SpecificHeat 对象的成员与 [SpecificHeat](pt01ch29pyo95.md#ker-specificheat-specificheat-pyc) 方法的参数具有相同的名称和描述。

### 29.95.4 对应的分析关键字

| [*SPECIFIC HEAT](../key/key-link.md#usb-kws-mspecificheat) |
| --- |
