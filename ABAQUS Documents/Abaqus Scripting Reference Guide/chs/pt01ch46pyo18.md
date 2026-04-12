# 46.18 PEGSection 对象

PEGSection 对象定义实体截面的属性。

PEGSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.18.1 PEGSection(...)

此方法创建 PEGSection 对象。

**Path**

```
mdb.models[*name*].PEGSection
session.odbs[*name*].PEGSection
```

**必需参数**

*name*

String，指定存储库键。

*material*

String，指定材料名称。

**可选参数**

*thickness*

Float，指定截面的厚度。可能的值为 *thickness* ![](../graphics/ker_eqn00060.gif) 0.0。默认值为 1.0。

*wedgeAngle1*

Float，指定边界平面之间角度的 x 分量，![](../graphics/ker_eqn00415.gif)。默认值为 0.0。

*wedgeAngle2*

Float，指定边界平面之间角度的 y 分量，![](../graphics/ker_eqn00416.gif)。默认值为 0.0。

**返回值**

PEGSection 对象。

**异常**

InvalidNameError 和 RangeError。

### 46.18.2 setValues(...)

此方法修改 PEGSection 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [PEGSection](pt01ch46pyo18.md#ker-pegsection-pegsection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 46.18.3 成员

PEGSection 对象的成员与 [PEGSection](pt01ch46pyo18.md#ker-pegsection-pegsection-pyc) 方法的参数具有相同的名称和描述。

### 46.18.4 对应分析关键字

| [*SOLID SECTION*](../key/key-link.md#usb-kws-msolidsection) |
| --- |
