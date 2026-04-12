# 29.71 MoistureSwelling 对象





MoistureSwelling 对象定义湿胀。

**访问**

```
import material
mdb.models[*name*].materials[*name*].moistureSwelling
import odbMaterial
session.odbs[*name*].materials[*name*].moistureSwelling
```

### 29.71.1 MoistureSwelling(...)

此方法创建 MoistureSwelling 对象。

**路径**

```
mdb.models[*name*].materials[*name*].MoistureSwelling
session.odbs[*name*].materials[*name*].MoistureSwelling
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

无。

**表格数据**

- 体积湿胀应变，![](../graphics/ker_eqn00294.gif)。
- 饱和度，![](../graphics/ker_eqn00234.gif)。此值必须在范围内 ![](../graphics/ker_eqn00295.gif)。

**返回值**

一个 MoistureSwelling 对象。

**异常**

无。

### 29.71.2 setValues(...)

此方法修改 MoistureSwelling 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [MoistureSwelling](pt01ch29pyo71.md#ker-moistureswelling-moistureswelling-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.71.3 成员

MoistureSwelling 对象具有与 [MoistureSwelling](pt01ch29pyo71.md#ker-moistureswelling-moistureswelling-pyc) 方法参数同名的成员，描述也相同。

此外，MoistureSwelling 对象可以具有以下成员：

*ratios*

一个 [Ratios](pt01ch29pyo86.md) 对象。

### 29.71.4 对应的分析关键字

| [*MOISTURE SWELLING](../key/key-link.md#usb-kws-mmoistureswell) |
| --- |




