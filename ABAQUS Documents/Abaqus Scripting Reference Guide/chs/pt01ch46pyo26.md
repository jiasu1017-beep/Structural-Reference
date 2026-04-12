# 46.26 TrussSection 对象





TrussSection 对象定义桁架截面的属性。

TrussSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.26.1 TrussSection(...)

此方法创建 TrussSection 对象。

**路径**

```
mdb.models[*name*].TrussSection
session.odbs[*name*].TrussSection
```

**必要参数**

*name*

String，指定存储库键。

*material*

String，指定材料的名称。

**可选参数**

*area*

Float，指定截面的横截面积。可能的值为 *area* ![](../graphics/ker_eqn00060.gif) 0。默认值为 1.0。

**返回值**

TrussSection 对象。

**异常**

RangeError 和 InvalidNameError。

### 46.26.2 setValues(...)

此方法修改 TrussSection 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [TrussSection](pt01ch46pyo26.md#ker-trusssection-trusssection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 46.26.3 成员

TrussSection 对象的成员与 [TrussSection](pt01ch46pyo26.md#ker-trusssection-trusssection-pyc) 方法的参数具有相同的名称和描述。

### 46.26.4 对应分析关键字

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |


