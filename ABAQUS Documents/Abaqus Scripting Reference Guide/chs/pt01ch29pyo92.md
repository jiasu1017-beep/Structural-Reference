# 29.92 Solubility 对象

Solubility 对象指定溶解度。

**访问**

```
import material
mdb.models[*name*].materials[*name*].solubility
import odbMaterial
session.odbs[*name*].materials[*name*].solubility
```

### 29.92.1 Solubility(...)

此方法创建 Solubility 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Solubility
session.odbs[*name*].materials[*name*].Solubility
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

- 溶解度。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

Solubility 对象。

**异常**

RangeError。

### 29.92.2 setValues(...)

此方法修改 Solubility 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Solubility](pt01ch29pyo92.md#ker-solubility-solubility-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.92.3 成员

Solubility 对象的成员与 [Solubility](pt01ch29pyo92.md#ker-solubility-solubility-pyc) 方法的参数具有相同的名称和描述。

### 29.92.4 对应的分析关键字

| [*SOLUBILITY](../key/key-link.md#usb-kws-msolubility) |
| --- |
