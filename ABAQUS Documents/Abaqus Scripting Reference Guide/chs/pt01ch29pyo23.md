# 29.23 ConcreteTensionStiffening 对象





ConcreteTensionStiffening 对象指定混凝土损伤塑性模型的硬化。

**访问**

```
import material
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteTensionStiffening
import odbMaterial
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteTensionStiffening
```

### 29.23.1 ConcreteTensionStiffening(...)

此方法创建 ConcreteTensionStiffening 对象。

**路径**

```
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteTensionStiffening
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteTensionStiffening
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*rate*

一个 Boolean，指定数据是否依赖于速率。默认值为 OFF。

*type*

一个 SymbolicConstant，指定裂后行为数据的类型。可能的值为：
- STRAIN，指定裂后应力为裂隙应变的函数。
- DISPLACEMENT，指定裂后应力为裂隙位移的函数。
- GFI，指定失效应力为断裂能的函数。

默认值为 STRAIN。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**表格数据**

如果 *type*=STRAIN，表格数据指定以下内容：
- 裂隙后的剩余直接应力，![](../graphics/ker_eqn00104.gif)。
- 直接裂隙应变，![](../graphics/ker_eqn00137.gif)。
- 直接裂隙应变率，![](../graphics/ker_eqn00139.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，表格数据指定以下内容：
- 裂隙后的剩余直接应力，![](../graphics/ker_eqn00104.gif)。
- 直接裂隙位移，![](../graphics/ker_eqn00138.gif)。
- 直接裂隙位移率，![](../graphics/ker_eqn00140.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=GFI，表格数据指定以下内容：
- 失效应力，![](../graphics/ker_eqn00141.gif)。
- 断裂能，![](../graphics/ker_eqn00142.gif)。
- 直接裂隙位移率，![](../graphics/ker_eqn00140.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ConcreteTensionStiffening 对象。

**异常**

RangeError。

### 29.23.2 setValues(...)

此方法修改 ConcreteTensionStiffening 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConcreteTensionStiffening](pt01ch29pyo23.md#ker-concretetensionstiffening-concretetensionstiffening-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.23.3 成员

ConcreteTensionStiffening 对象具有与 [ConcreteTensionStiffening](pt01ch29pyo23.md#ker-concretetensionstiffening-concretetensionstiffening-pyc) 方法参数同名的成员，描述也相同。

### 29.23.4 对应的分析关键字

| [*CONCRETE TENSION STIFFENING](../key/key-link.md#usb-kws-mconcretetensstiff) |
| --- |




