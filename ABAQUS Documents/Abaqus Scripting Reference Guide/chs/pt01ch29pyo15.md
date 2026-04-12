# 29.15 ClayHardening 对象





ClayHardening 对象指定粘土塑性模型的硬化。

**访问**

```
import material
mdb.models[*name*].materials[*name*].clayPlasticity.clayHardening
import odbMaterial
session.odbs[*name*].materials[*name*].clayPlasticity.clayHardening
```

### 29.15.1 ClayHardening(...)

此方法创建 ClayHardening 对象。

**路径**

```
mdb.models[*name*].materials[*name*].clayPlasticity.ClayHardening
session.odbs[*name*].materials[*name*].clayPlasticity.ClayHardening
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

- 屈服时的静水压力应力，![](../graphics/ker_eqn00105.gif)。
- 对应体积塑性应变的绝对值。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ClayHardening 对象。

**异常**

RangeError。

### 29.15.2 setValues(...)

此方法修改 ClayHardening 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ClayHardening](pt01ch29pyo15.md#ker-clayhardening-clayhardening-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.15.3 成员

ClayHardening 对象具有与 [ClayHardening](pt01ch29pyo15.md#ker-clayhardening-clayhardening-pyc) 方法参数同名的成员，描述也相同。

### 29.15.4 对应的分析关键字

| [*CLAY HARDENING](../key/key-link.md#usb-kws-mclayhardening) |
| --- |




