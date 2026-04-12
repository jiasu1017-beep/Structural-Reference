# 29.86 Ratios 对象

Ratios 对象指定定义各向异性膨胀的比率。

**访问**

```
import material
mdb.models[*name*].materials[*name*].moistureSwelling.ratios
mdb.models[*name*].materials[*name*].swelling.ratios
import odbMaterial
session.odbs[*name*].materials[*name*].moistureSwelling.ratios
session.odbs[*name*].materials[*name*].swelling.ratios
```

### 29.86.1 Ratios(...)

此方法创建 Ratios 对象。

**路径**

```
mdb.models[*name*].materials[*name*].moistureSwelling.Ratios
mdb.models[*name*].materials[*name*].swelling.Ratios
session.odbs[*name*].materials[*name*].moistureSwelling.Ratios
session.odbs[*name*].materials[*name*].swelling.Ratios
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

- ![](../graphics/ker_eqn00359.gif)。
- ![](../graphics/ker_eqn00360.gif)。
- ![](../graphics/ker_eqn00361.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

Ratios 对象。

**异常**

RangeError。

### 29.86.2 setValues(...)

此方法修改 Ratios 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Ratios](pt01ch29pyo86.md#ker-ratios-ratios-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.86.3 成员

Ratios 对象的成员与 [Ratios](pt01ch29pyo86.md#ker-ratios-ratios-pyc) 方法的参数具有相同的名称和描述。

### 29.86.4 对应的分析关键字

| [*RATIOS](../key/key-link.md#usb-kws-mswellratios) |
| --- |
