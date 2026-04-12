# 29.41 Diffusivity 对象





Diffusivity 对象指定质量扩散率。

**访问**

```
import material
mdb.models[*name*].materials[*name*].diffusivity
import odbMaterial
session.odbs[*name*].materials[*name*].diffusivity
```

### 29.41.1 Diffusivity(...)

此方法创建 Diffusivity 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Diffusivity
session.odbs[*name*].materials[*name*].Diffusivity
```

**必需参数**

*table*

一个 Float 元组序列，指定如下所述的项目。

**可选参数**

*type*

一个 SymbolicConstant，指定扩散率类型。可能的值为 ISOTROPIC、ORTHOTROPIC 和 ANISOTROPIC。默认值为 ISOTROPIC。

*law*

一个 SymbolicConstant，指定扩散行为。可能的值为 GENERAL 和 FICK。默认值为 GENERAL。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

如果 *type*=ISOTROPIC，表格数据指定以下内容：
- 扩散率，![](../graphics/ker_eqn00172.gif)。
- 浓度，![](../graphics/ker_eqn00173.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ORTHOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00174.gif)。
- ![](../graphics/ker_eqn00031.gif)。
- ![](../graphics/ker_eqn00034.gif)。
- 浓度，![](../graphics/ker_eqn00173.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ANISOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00174.gif)。
- ![](../graphics/ker_eqn00175.gif)。
- ![](../graphics/ker_eqn00031.gif)。
- ![](../graphics/ker_eqn00176.gif)。
- ![](../graphics/ker_eqn00032.gif)。
- ![](../graphics/ker_eqn00034.gif)。
- 浓度，![](../graphics/ker_eqn00173.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Diffusivity 对象。

**异常**

RangeError。

### 29.41.2 setValues(...)

此方法修改 Diffusivity 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Diffusivity](pt01ch29pyo41.md#ker-diffusivity-diffusivity-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.41.3 成员

Diffusivity 对象具有与 [Diffusivity](pt01ch29pyo41.md#ker-diffusivity-diffusivity-pyc) 方法参数同名的成员，描述也相同。

此外，Diffusivity 对象可以具有以下成员：

*pressureEffect*

一个 [PressureEffect](pt01ch29pyo84.md) 对象。

*soretEffect*

一个 [SoretEffect](pt01ch29pyo93.md) 对象。

### 29.41.4 对应的分析关键字

| [*DIFFUSIVITY](../key/key-link.md#usb-kws-mdiffusivity) |
| --- |




