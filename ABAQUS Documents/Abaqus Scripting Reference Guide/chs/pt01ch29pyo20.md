# 29.20 ConcreteCompressionHardening 对象





ConcreteCompressionHardening 对象指定混凝土损伤塑性模型的硬化。

**访问**

```
import material
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteCompressionHardening
import odbMaterial
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteCompressionHardening
```

### 29.20.1 ConcreteCompressionHardening(...)

此方法创建 ConcreteCompressionHardening 对象。

**路径**

```
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteCompressionHardening
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteCompressionHardening
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*rate*

一个 Boolean，指定数据是否依赖于速率。默认值为 OFF。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**表格数据**

- 压缩屈服应力，![](../graphics/ker_eqn00102.gif)。
- 非弹性（压碎）应变，![](../graphics/ker_eqn00130.gif)。
- 非弹性（压碎）应变率，![](../graphics/ker_eqn00131.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ConcreteCompressionHardening 对象。

**异常**

RangeError。

### 29.20.2 setValues(...)

此方法修改 ConcreteCompressionHardening 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConcreteCompressionHardening](pt01ch29pyo20.md#ker-concretecompressionhardening-concretecompressionhard-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.20.3 成员

ConcreteCompressionHardening 对象具有与 [ConcreteCompressionHardening](pt01ch29pyo20.md#ker-concretecompressionhardening-concretecompressionhard-pyc) 方法参数同名的成员，描述也相同。

### 29.20.4 对应的分析关键字

| [*CONCRETE COMPRESSION HARDENING](../key/key-link.md#usb-kws-mconcretecomphard) |
| --- |




