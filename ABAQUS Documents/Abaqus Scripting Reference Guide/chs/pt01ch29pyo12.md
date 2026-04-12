# 29.12 CastIronCompressionHardening 对象





CastIronCompressionHardening 对象指定铸铁塑性模型的硬化。

**访问**

```
import material
mdb.models[*name*].materials[*name*].castIronPlasticity\
.castIronCompressionHardening
import odbMaterial
session.odbs[*name*].materials[*name*].castIronPlasticity\
.castIronCompressionHardening
```

### 29.12.1 CastIronCompressionHardening(...)

此方法创建 CastIronCompressionHardening 对象。

**路径**

```
mdb.models[*name*].materials[*name*].castIronPlasticity\
.CastIronCompressionHardening
session.odbs[*name*].materials[*name*].castIronPlasticity\
.CastIronCompressionHardening
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

- 压缩屈服应力，![](../graphics/ker_eqn00102.gif)。
- 对应塑性应变的绝对值。（输入的第一个表格值必须始终为零。）
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CastIronCompressionHardening 对象。

**异常**

RangeError。

### 29.12.2 setValues(...)

此方法修改 CastIronCompressionHardening 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CastIronCompressionHardening](pt01ch29pyo12.md#ker-castironcompressionhardening-castironcompressionhard-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.12.3 成员

CastIronCompressionHardening 对象具有与 [CastIronCompressionHardening](pt01ch29pyo12.md#ker-castironcompressionhardening-castironcompressionhard-pyc) 方法参数同名的成员，描述也相同。

### 29.12.4 对应的分析关键字

| [*CAST IRON COMPRESSION HARDENING](../key/key-link.md#usb-kws-mcastironcomhardening) |
| --- |




