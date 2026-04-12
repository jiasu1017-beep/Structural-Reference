# 29.96 Swelling 对象

Swelling 对象指定材料的时间依赖性体积膨胀。

**访问**

```
import material
mdb.models[*name*].materials[*name*].swelling
import odbMaterial
session.odbs[*name*].materials[*name*].swelling
```

### 29.96.1 Swelling(...)

此方法创建 Swelling 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Swelling
session.odbs[*name*].materials[*name*].Swelling
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

此参数仅在 *law*=INPUT 时有效。

**可选参数**

*law*

SymbolicConstant，指定定义膨胀行为的数据类型。可能的值为 INPUT 和 USER。默认值为 INPUT。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

- 体积膨胀应变率。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

Swelling 对象。

**异常**

RangeError。

### 29.96.2 setValues(...)

此方法修改 Swelling 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Swelling](pt01ch29pyo96.md#ker-swelling-swelling-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.96.3 成员

Swelling 对象的成员与 [Swelling](pt01ch29pyo96.md#ker-swelling-swelling-pyc) 方法的参数具有相同的名称和描述。

此外，Swelling 对象可以具有以下成员：

*ratios*

[Ratios](pt01ch29pyo86.md) 对象。

### 29.96.4 对应的分析关键字

| [*SWELLING](../key/key-link.md#usb-kws-mswelling) |
| --- |
