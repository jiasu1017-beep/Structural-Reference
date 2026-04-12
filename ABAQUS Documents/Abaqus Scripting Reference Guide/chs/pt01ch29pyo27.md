# 29.27 CrushableFoam 对象





CrushableFoam 对象指定可压碎泡沫塑性模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].crushableFoam
import odbMaterial
session.odbs[*name*].materials[*name*].crushableFoam
```

### 29.27.1 CrushableFoam(...)

此方法创建 CrushableFoam 对象。

**路径**

```
mdb.models[*name*].materials[*name*].CrushableFoam
session.odbs[*name*].materials[*name*].CrushableFoam
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*hardening*

一个 SymbolicConstant，指定硬化/软化定义类型。可能的值为 VOLUMETRIC 和 ISOTROPIC。默认值为 VOLUMETRIC。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**表格数据**

如果 *hardening*=VOLUMETRIC，表格数据指定以下内容：
- 单轴压缩初始屈服应力 ![](../graphics/ker_eqn00152.gif) 与静水压缩初始屈服应力 ![](../graphics/ker_eqn00153.gif) 的比值 ![](../graphics/ker_eqn00143.gif)；0.0 ![](../graphics/ker_eqn00154.gif) 3.0。
- 静水拉伸屈服应力 ![](../graphics/ker_eqn00156.gif) 与静水压缩初始屈服应力 ![](../graphics/ker_eqn00153.gif) 的比值 ![](../graphics/ker_eqn00155.gif)。默认值为 1.0。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *hardening*=ISOTROPIC，表格数据指定以下内容：
- 单轴压缩初始屈服应力 ![](../graphics/ker_eqn00152.gif) 与静水压缩初始屈服应力 ![](../graphics/ker_eqn00153.gif) 的比值 ![](../graphics/ker_eqn00143.gif)；0.0 ![](../graphics/ker_eqn00157.gif) 3.0。
- 塑性泊松比。![](../graphics/ker_eqn00158.gif)；-1![](../graphics/ker_eqn00159.gif)0.5。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CrushableFoam 对象。

**异常**

RangeError。

### 29.27.2 setValues(...)

此方法修改 CrushableFoam 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CrushableFoam](pt01ch29pyo27.md#ker-crushablefoam-crushablefoam-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.27.3 成员

CrushableFoam 对象具有与 [CrushableFoam](pt01ch29pyo27.md#ker-crushablefoam-crushablefoam-pyc) 方法参数同名的成员，描述也相同。

此外，CrushableFoam 对象可以具有以下成员：

*crushableFoamHardening*

一个 [CrushableFoamHardening](pt01ch29pyo28.md) 对象。

*rateDependent*

一个 [RateDependent](pt01ch29pyo85.md) 对象。

### 29.27.4 对应的分析关键字

| [*CRUSHABLE FOAM](../key/key-link.md#usb-kws-mcrushfoam) |
| --- |




