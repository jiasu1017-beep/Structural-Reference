# 46.14 HomogeneousSolidSection 对象

HomogeneousSolidSection 对象定义实体截面的属性。

HomogeneousSolidSection 对象派生自 [SolidSection](pt01ch46pyo22.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.14.1 HomogeneousSolidSection(...)

此方法创建 HomogeneousSolidSection 对象。

**Path**

```
mdb.models[*name*].HomogeneousSolidSection
session.odbs[*name*].HomogeneousSolidSection
```

**必需参数**

*name*

String，指定存储库键。

*material*

String，指定材料名称。

**可选参数**

*thickness*

`None` 或 Float，指定截面的厚度。可能的值为 None 或浮点值 such that *thickness* ![](../graphics/ker_eqn00060.gif) 0.0。默认值为 None。

**返回值**

HomogeneousSolidSection 对象。

**异常**

InvalidNameError 和 RangeError。

### 46.14.2 setValues(...)

此方法修改 HomogeneousSolidSection 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [HomogeneousSolidSection](pt01ch46pyo14.md#ker-homogeneoussolidsection-homogeneoussolidsection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 46.14.3 成员

HomogeneousSolidSection 对象的成员与 [HomogeneousSolidSection](pt01ch46pyo14.md#ker-homogeneoussolidsection-homogeneoussolidsection-pyc) 方法的参数具有相同的名称和描述。

### 46.14.4 对应分析关键字

| [*SOLID SECTION*](../key/key-link.md#usb-kws-msolidsection) |
| --- |
