# 29.19 ConcreteCompressionDamage 对象





ConcreteCompressionDamage 对象指定混凝土损伤塑性模型的硬化。

**访问**

```
import material
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteCompressionDamage
import odbMaterial
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteCompressionDamage
```

### 29.19.1 ConcreteCompressionDamage(...)

此方法创建 ConcreteCompressionDamage 对象。

**路径**

```
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteCompressionDamage
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteCompressionDamage
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*tensionRecovery*

一个 Float，指定刚度恢复因子 ![](../graphics/ker_eqn00127.gif) 的值，该因子决定当加载从压缩变为拉伸时恢复的张拉刚度量。默认值为 0.0。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**表格数据**

- 压缩损伤变量，![](../graphics/ker_eqn00128.gif)。
- 非弹性（压碎）应变，![](../graphics/ker_eqn00129.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ConcreteCompressionDamage 对象。

**异常**

RangeError。

### 29.19.2 setValues(...)

此方法修改 ConcreteCompressionDamage 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConcreteCompressionDamage](pt01ch29pyo19.md#ker-concretecompressiondamage-concretecompressiondamage-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.19.3 成员

ConcreteCompressionDamage 对象具有与 [ConcreteCompressionDamage](pt01ch29pyo19.md#ker-concretecompressiondamage-concretecompressiondamage-pyc) 方法参数同名的成员，描述也相同。

### 29.19.4 对应的分析关键字

| [*CONCRETE COMPRESSION DAMAGE](../key/key-link.md#usb-kws-mconcretecompdamage) |
| --- |




