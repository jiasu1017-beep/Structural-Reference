# 29.36 DeformationPlasticity 对象





DeformationPlasticity 对象指定变形塑性模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].deformationPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].deformationPlasticity
```

### 29.36.1 DeformationPlasticity(...)

此方法创建 DeformationPlasticity 对象。

**路径**

```
mdb.models[*name*].materials[*name*].DeformationPlasticity
session.odbs[*name*].materials[*name*].DeformationPlasticity
```

**必需参数**

*table*

一个 Float 元组序列，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

**表格数据**

- 杨氏模量，![](../graphics/ker_eqn00163.gif)。
- 泊松比，![](../graphics/ker_eqn00164.gif)。
- 屈服应力，![](../graphics/ker_eqn00165.gif)。
- 指数，![](../graphics/ker_eqn00088.gif)。
- 屈服偏移，![](../graphics/ker_eqn00090.gif)。
- 温度（如果数据依赖于温度）。

**返回值**

一个 DeformationPlasticity 对象。

**异常**

RangeError。

### 29.36.2 setValues(...)

此方法修改 DeformationPlasticity 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DeformationPlasticity](pt01ch29pyo36.md#ker-deformationplasticity-deformationplasticity-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.36.3 成员

DeformationPlasticity 对象具有与 [DeformationPlasticity](pt01ch29pyo36.md#ker-deformationplasticity-deformationplasticity-pyc) 方法参数同名的成员，描述也相同。

### 29.36.4 对应的分析关键字

| [*DEFORMATION PLASTICITY](../key/key-link.md#usb-kws-mdeformplas) |
| --- |




