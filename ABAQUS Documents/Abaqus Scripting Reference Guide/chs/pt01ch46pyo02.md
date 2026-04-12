# 46.2 AcousticInfiniteSection 对象

AcousticInfiniteSection 对象定义声学截面的属性。

AcousticInfiniteSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.2.1 AcousticInfiniteSection(...)

此方法创建 AcousticInfiniteSection 对象。

**Path**

```
mdb.models[*name*].AcousticInfiniteSection
session.odbs[*name*].AcousticInfiniteSection
```

**必需参数**

*name*

 String，指定存储库键。

*material*

 String，指定材料名称。

**可选参数**

*thickness*

 Float，指定截面厚度。可能的值为 *thickness* ![](../graphics/ker_eqn00060.gif) 0.0。默认值为 1.0。

*order*

 Int，指定将用于解析无限方向声场变化的九阶多项式的数量。可能的值为 0 ![](../graphics/ker_eqn00048.gif) *order* ![](../graphics/ker_eqn00013.gif) 10。默认值为 10。

**返回值**

AcousticInfiniteSection 对象。

**异常**

InvalidNameError 和 RangeError。

### 46.2.2 setValues(...)

此方法修改 AcousticInfiniteSection 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [AcousticInfiniteSection](pt01ch46pyo02.md#ker-acousticinfinitesection-acousticinfinitesection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 46.2.3 成员

AcousticInfiniteSection 对象的成员与 [AcousticInfiniteSection](pt01ch46pyo02.md#ker-acousticinfinitesection-acousticinfinitesection-pyc) 方法的参数具有相同的名称和描述。

### 46.2.4 对应分析关键字

| [*SOLID SECTION*](../key/key-link.md#usb-kws-msolidsection) |
| --- |

