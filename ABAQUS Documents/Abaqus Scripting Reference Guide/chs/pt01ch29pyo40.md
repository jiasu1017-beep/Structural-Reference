# 29.40 Dielectric 对象





Dielectric 对象指定介电材料属性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].dielectric
import odbMaterial
session.odbs[*name*].materials[*name*].dielectric
```

### 29.40.1 Dielectric(...)

此方法创建 Dielectric 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Dielectric
session.odbs[*name*].materials[*name*].Dielectric
```

**必需参数**

*table*

一个 Float 元组序列，指定如下所述的项目。

**可选参数**

*type*

一个 SymbolicConstant，指定介电行为类型。可能的值为 ISOTROPIC、ORTHOTROPIC 和 ANISOTROPIC。默认值为 ISOTROPIC。

*frequencyDependency*

一个 Boolean，指定数据是否依赖于频率。默认值为 OFF。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

如果 *type*=ISOTROPIC，表格数据指定以下内容：
- 介电常数。
- 频率（如果数据依赖于频率）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ORTHOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00166.gif)。
- ![](../graphics/ker_eqn00167.gif)。
- ![](../graphics/ker_eqn00168.gif)。
- 频率（如果数据依赖于频率）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ANISOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00166.gif)。
- ![](../graphics/ker_eqn00169.gif)。
- ![](../graphics/ker_eqn00167.gif)。
- ![](../graphics/ker_eqn00170.gif)。
- ![](../graphics/ker_eqn00171.gif)。
- ![](../graphics/ker_eqn00168.gif)。
- 频率（如果数据依赖于频率）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Dielectric 对象。

**异常**

无。

### 29.40.2 setValues(...)

此方法修改 Dielectric 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Dielectric](pt01ch29pyo40.md#ker-dielectric-dielectric-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.40.3 成员

Dielectric 对象具有与 [Dielectric](pt01ch29pyo40.md#ker-dielectric-dielectric-pyc) 方法参数同名的成员，描述也相同。

### 29.40.4 对应的分析关键字

| [*DIELECTRIC](../key/key-link.md#usb-kws-mdielectric) |
| --- |




