# 29.69 MohrCoulombHardening 对象

MohrCoulombHardening 对象指定摩尔-库仑塑性模型的硬化。

**访问**

```
import material
mdb.models[*name*].materials[*name*].mohrCoulombPlasticity\
.mohrCoulombHardening
import odbMaterial
session.odbs[*name*].materials[*name*].mohrCoulombPlasticity\
.mohrCoulombHardening
```

### 29.69.1 MohrCoulombHardening(...)

此方法创建 MohrCoulombHardening 对象。

**路径**

```
mdb.models[*name*].materials[*name*].mohrCoulombPlasticity\
.MohrCoulombHardening
session.odbs[*name*].materials[*name*].mohrCoulombPlasticity\
.MohrCoulombHardening
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

- 内聚屈服应力。
- 对应塑性应变的绝对值。（输入的第一个表格值必须始终为零。）
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

MohrCoulombHardening 对象。

**异常**

RangeError。

### 29.69.2 setValues(...)

此方法修改 MohrCoulombHardening 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [MohrCoulombHardening](pt01ch29pyo69.md#ker-mohrcoulombhardening-mohrcoulombhardening-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.69.3 成员

MohrCoulombHardening 对象的成员与 [MohrCoulombHardening](pt01ch29pyo69.md#ker-mohrcoulombhardening-mohrcoulombhardening-pyc) 方法的参数具有相同的名称和描述。

### 29.69.4 对应的分析关键字

| [*MOHR COULOMB HARDENING](../key/key-link.md#usb-kws-mmohrcoulombhardening) |
| --- |
