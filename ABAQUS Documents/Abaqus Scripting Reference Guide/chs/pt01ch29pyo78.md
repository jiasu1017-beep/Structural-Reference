# 29.78 PoreFluidExpansion 对象

PoreFluidExpansion 对象指定液压流体的热膨胀系数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].poreFluidExpansion
import odbMaterial
session.odbs[*name*].materials[*name*].poreFluidExpansion
```

### 29.78.1 PoreFluidExpansion(...)

此方法创建 PoreFluidExpansion 对象。

**路径**

```
mdb.models[*name*].materials[*name*].PoreFluidExpansion
session.odbs[*name*].materials[*name*].PoreFluidExpansion
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*zero*

Float，指定 ![](../graphics/ker_eqn00061.gif) 的值。默认值为 0.0。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

- 平均热膨胀系数，![](../graphics/ker_eqn00239.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

PoreFluidExpansion 对象。

**异常**

RangeError。

### 29.78.2 setValues(...)

此方法修改 PoreFluidExpansion 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [PoreFluidExpansion](pt01ch29pyo78.md#ker-porefluidexpansion-porefluidexpansion-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.78.3 成员

PoreFluidExpansion 对象的成员与 [PoreFluidExpansion](pt01ch29pyo78.md#ker-porefluidexpansion-porefluidexpansion-pyc) 方法的参数具有相同的名称和描述。

### 29.78.4 对应的分析关键字

| [*EXPANSION](../key/key-link.md#usb-kws-mexpansion) |
| --- |
