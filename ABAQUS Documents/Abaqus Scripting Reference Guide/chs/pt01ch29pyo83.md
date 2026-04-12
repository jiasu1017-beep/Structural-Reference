# 29.83 Potential 对象

Potential 对象定义各向异性屈服/蠕变模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].creep.potential
mdb.models[*name*].materials[*name*].plastic.potential
mdb.models[*name*].materials[*name*].viscous.potential
import odbMaterial
session.odbs[*name*].materials[*name*].creep.potential
session.odbs[*name*].materials[*name*].plastic.potential
session.odbs[*name*].materials[*name*].viscous.potential
```

### 29.83.1 Potential(...)

此方法创建 Potential 对象。

**路径**

```
mdb.models[*name*].materials[*name*].creep.Potential
mdb.models[*name*].materials[*name*].plastic.Potential
mdb.models[*name*].materials[*name*].viscous.Potential
session.odbs[*name*].materials[*name*].creep.Potential
session.odbs[*name*].materials[*name*].plastic.Potential
session.odbs[*name*].materials[*name*].viscous.Potential
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

- ![](../graphics/ker_eqn00350.gif)。
- ![](../graphics/ker_eqn00351.gif)。
- ![](../graphics/ker_eqn00352.gif)。
- ![](../graphics/ker_eqn00353.gif)。
- ![](../graphics/ker_eqn00354.gif)。
- ![](../graphics/ker_eqn00355.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

Potential 对象。

**异常**

RangeError。

### 29.83.2 setValues(...)

此方法修改 Potential 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Potential](pt01ch29pyo83.md#ker-potential-potential-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.83.3 成员

Potential 对象的成员与 [Potential](pt01ch29pyo83.md#ker-potential-potential-pyc) 方法的参数具有相同的名称和描述。

### 29.83.4 对应的分析关键字

| [*POTENTIAL](../key/key-link.md#usb-kws-mpotential) |
| --- |
