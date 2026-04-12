# 29.26 Creep 对象





Creep 对象定义蠕变规律。

**访问**

```
import material
mdb.models[*name*].materials[*name*].creep
import odbMaterial
session.odbs[*name*].materials[*name*].creep
```

### 29.26.1 Creep(...)

此方法创建 Creep 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Creep
session.odbs[*name*].materials[*name*].Creep
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*law*

一个 SymbolicConstant，指定应变硬化规律。可能的值为 STRAIN、TIME、HYPERBOLIC_SINE 和 USER。默认值为 STRAIN。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**表格数据**

如果 *law*=STRAIN 或 *law*=TIME，表格数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。
- ![](../graphics/ker_eqn00088.gif)。
- ![](../graphics/ker_eqn00089.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *law*=HYPERBOLIC_SINE，表格数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。
- ![](../graphics/ker_eqn00150.gif)。
- ![](../graphics/ker_eqn00088.gif)。
- ![](../graphics/ker_eqn00151.gif)（如果数据依赖于温度）。
- ![](../graphics/ker_eqn00096.gif)。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Creep 对象。

**异常**

RangeError。

### 29.26.2 setValues(...)

此方法修改 Creep 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Creep](pt01ch29pyo26.md#ker-creep-creep-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.26.3 成员

Creep 对象具有与 [Creep](pt01ch29pyo26.md#ker-creep-creep-pyc) 方法参数同名的成员，描述也相同。

此外，Creep 对象可以具有以下成员：

*ornl*

一个 [Ornl](pt01ch29pyo73.md) 对象。

*potential*

一个 [Potential](pt01ch29pyo83.md) 对象。

### 29.26.4 对应的分析关键字

| [*CREEP](../key/key-link.md#usb-kws-mcreep) |
| --- |




