# 29.80 PorousElastic 对象

PorousElastic 对象指定多孔材料的弹性材料属性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].porousElastic
import odbMaterial
session.odbs[*name*].materials[*name*].porousElastic
```

### 29.80.1 PorousElastic(...)

此方法创建 PorousElastic 对象。

**路径**

```
mdb.models[*name*].materials[*name*].PorousElastic
session.odbs[*name*].materials[*name*].PorousElastic
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*shear*

SymbolicConstant，指定剪切定义形式。可能的值为 G 和 POISSON。默认值为 POISSON。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

如果 *shear*=G，表格数据指定以下内容：
- 对数体积模量，![](../graphics/ker_eqn00342.gif)。（无量纲。）
- 剪切模量，![](../graphics/ker_eqn00182.gif)。
- 弹性拉伸极限，![](../graphics/ker_eqn00343.gif)。（此值不能为负。）
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *shear*=POISSON，表格数据指定以下内容：
- 对数体积模量，![](../graphics/ker_eqn00342.gif)。（无量纲。）
- 泊松比，![](../graphics/ker_eqn00164.gif)。
- 弹性拉伸极限，![](../graphics/ker_eqn00343.gif)。（此值不能为负。）
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

PorousElastic 对象。

**异常**

RangeError。

### 29.80.2 setValues(...)

此方法修改 PorousElastic 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [PorousElastic](pt01ch29pyo80.md#ker-porouselastic-porouselastic-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.80.3 成员

PorousElastic 对象的成员与 [PorousElastic](pt01ch29pyo80.md#ker-porouselastic-porouselastic-pyc) 方法的参数具有相同的名称和描述。

### 29.80.4 对应的分析关键字

| [*POROUS ELASTIC](../key/key-link.md#usb-kws-mporouselastic) |
| --- |
