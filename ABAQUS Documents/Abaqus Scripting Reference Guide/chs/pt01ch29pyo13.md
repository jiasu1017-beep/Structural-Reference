# 29.13 CastIronPlasticity 对象





CastIronPlasticity 对象指定铸铁塑性模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].castIronPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].castIronPlasticity
```

### 29.13.1 CastIronPlasticity(...)

此方法创建 CastIronPlasticity 对象。

**路径**

```
mdb.models[*name*].materials[*name*].CastIronPlasticity
session.odbs[*name*].materials[*name*].CastIronPlasticity
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
- 塑性泊松比，![](../graphics/ker_eqn00103.gif)（无量纲）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CastIronPlasticity 对象。

**异常**

RangeError。

### 29.13.2 setValues(...)

此方法修改 CastIronPlasticity 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CastIronPlasticity](pt01ch29pyo13.md#ker-castironplasticity-castironplasticity-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.13.3 成员

CastIronPlasticity 对象具有与 [CastIronPlasticity](pt01ch29pyo13.md#ker-castironplasticity-castironplasticity-pyc) 方法参数同名的成员，描述也相同。

此外，CastIronPlasticity 对象可以具有以下成员：

*castIronTensionHardening*

一个 [CastIronTensionHardening](pt01ch29pyo14.md) 对象。

*castIronCompressionHardening*

一个 [CastIronCompressionHardening](pt01ch29pyo12.md) 对象。

### 29.13.4 对应的分析关键字

| [*CAST IRON PLASTICITY](../key/key-link.md#usb-kws-mcastironplastic) |
| --- |




