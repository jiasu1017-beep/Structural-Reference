# 29.22 ConcreteTensionDamage 对象





ConcreteTensionDamage 对象指定混凝土损伤塑性模型的硬化。

**访问**

```
import material
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteTensionDamage
import odbMaterial
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteTensionDamage
```

### 29.22.1 ConcreteTensionDamage(...)

此方法创建 ConcreteTensionDamage 对象。

**路径**

```
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteTensionDamage
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteTensionDamage
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*compressionRecovery*

一个 Float，指定刚度恢复因子 ![](../graphics/ker_eqn00135.gif) 的值，该因子决定当加载从拉伸变为压缩时恢复的压缩刚度量。默认值为 1.0。

*type*

一个 SymbolicConstant，指定拉伸损伤数据的类型。设置 *type*=STRAIN 以将拉伸损伤变量指定为裂隙应变的函数。设置 *type*=DISPLACEMENT 以将拉伸损伤变量指定为裂隙位移的函数。可能的值为 STRAIN 和 DISPLACEMENT。默认值为 STRAIN。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**表格数据**

如果 *type*=STRAIN，表格数据指定以下内容：
- 拉伸损伤变量，![](../graphics/ker_eqn00136.gif)。
- 直接裂隙应变，![](../graphics/ker_eqn00137.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，表格数据指定以下内容：
- 拉伸损伤变量，![](../graphics/ker_eqn00136.gif)。
- 直接裂隙位移，![](../graphics/ker_eqn00138.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ConcreteTensionDamage 对象。

**异常**

RangeError。

### 29.22.2 setValues(...)

此方法修改 ConcreteTensionDamage 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConcreteTensionDamage](pt01ch29pyo22.md#ker-concretetensiondamage-concretetensiondamage-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.22.3 成员

ConcreteTensionDamage 对象具有与 [ConcreteTensionDamage](pt01ch29pyo22.md#ker-concretetensiondamage-concretetensiondamage-pyc) 方法参数同名的成员，描述也相同。

### 29.22.4 对应的分析关键字

| [*CONCRETE TENSION DAMAGE](../key/key-link.md#usb-kws-mconcretetensdamage) |
| --- |




