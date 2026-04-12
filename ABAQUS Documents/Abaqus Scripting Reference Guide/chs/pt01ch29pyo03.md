# 29.3 AnnealTemperature 对象





AnnealTemperature 对象指定材料退火温度。

**访问**

```
import material
mdb.models[*name*].materials[*name*].plastic.annealTemperature
import odbMaterial
session.odbs[*name*].materials[*name*].plastic.annealTemperature
```

### 29.3.1 AnnealTemperature(...)

此方法创建 AnnealTemperature 对象。

**路径**

```
mdb.models[*name*].materials[*name*].plastic.AnnealTemperature
session.odbs[*name*].materials[*name*].plastic.AnnealTemperature
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**表格数据**

- 退火温度，![](../graphics/ker_eqn00053.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 AnnealTemperature 对象。

**异常**

RangeError。

### 29.3.2 setValues(...)

此方法修改 AnnealTemperature 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [AnnealTemperature](pt01ch29pyo03.md#ker-annealtemperature-annealtemperature-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.3.3 成员

AnnealTemperature 对象具有与 [AnnealTemperature](pt01ch29pyo03.md#ker-annealtemperature-annealtemperature-pyc) 方法参数同名的成员，描述也相同。

### 29.3.4 对应的分析关键字

| [*ANNEAL TEMPERATURE](../key/key-link.md#usb-kws-mannealtemp) |
| --- |




