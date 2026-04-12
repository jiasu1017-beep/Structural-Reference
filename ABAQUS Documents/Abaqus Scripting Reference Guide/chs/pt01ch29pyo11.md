# 29.11 CapPlasticity 对象





CapPlasticity 对象指定修改的 Drucker-Prager/帽盖塑性模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].capPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].capPlasticity
```

### 29.11.1 CapPlasticity(...)

此方法创建 CapPlasticity 对象。

**路径**

```
mdb.models[*name*].materials[*name*].CapPlasticity
session.odbs[*name*].materials[*name*].CapPlasticity
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

- 材料内聚力，![](../graphics/ker_eqn00082.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) 平面（Abaqus/Standard）或 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面（Abaqus/Explicit）中。
- 材料摩擦角，![](../graphics/ker_eqn00095.gif)，在 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) 平面（Abaqus/Standard）或 ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) 平面（Abaqus/Explicit）中。以度为单位提供值。
- 帽盖偏心率参数，![](../graphics/ker_eqn00096.gif)。其值必须大于零（通常为 0.0 ![](../graphics/ker_eqn00097.gif) 1.0）。
- 初始帽盖屈服面位置，![](../graphics/ker_eqn00098.gif)。
- 过渡面半径参数，![](../graphics/ker_eqn00090.gif)。默认值为 0.0（即无过渡面）。
- （在 Abaqus/Explicit 中不使用）![](../graphics/ker_eqn00099.gif)，三轴拉伸流动应力与三轴压缩流动应力的比值。可能的值为 0.778 ![](../graphics/ker_eqn00100.gif) 1.0。如果接受默认值 0.0，Abaqus/Standard 假设 ![](../graphics/ker_eqn00101.gif) 1.0。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CapPlasticity 对象。

**异常**

RangeError。

### 29.11.2 setValues(...)

此方法修改 CapPlasticity 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CapPlasticity](pt01ch29pyo11.md#ker-capplasticity-capplasticity-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.11.3 成员

CapPlasticity 对象具有与 [CapPlasticity](pt01ch29pyo11.md#ker-capplasticity-capplasticity-pyc) 方法参数同名的成员，描述也相同。

此外，CapPlasticity 对象可以具有以下成员：

*capCreepCohesion*

一个 [CapCreepCohesion](pt01ch29pyo08.md) 对象。

*capCreepConsolidation*

一个 [CapCreepConsolidation](pt01ch29pyo09.md) 对象。

*capHardening*

一个 [CapHardening](pt01ch29pyo10.md) 对象。

### 29.11.4 对应的分析关键字

| [*CAP PLASTICITY](../key/key-link.md#usb-kws-mcapplasticity) |
| --- |




