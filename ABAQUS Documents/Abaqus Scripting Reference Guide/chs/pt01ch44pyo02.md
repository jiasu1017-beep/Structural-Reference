# 44.2 CompositeLayup 对象

CompositeLayup 对象用于在零件上指定复合铺层。

**访问**

```
import part
mdb.models[*name*].parts[*name*].compositeLayups[*i*]
```

### 44.2.1 CompositeLayup(...)

此方法创建 CompositeLayup 对象。

**Path**

```
mdb.models[*name*].parts[*name*].CompositeLayups
```

**必需参数**

*name*

 String，指定存储库键。

**可选参数**

*description*

 String，指定复合铺层的描述。

*offsetType*

 SymbolicConstant，指定用于定义壳偏移的方法。如果 *offsetType*=OFFSET_FIELD，则需要 *offsetField* 参数。此成员仅在 *elementType*=SHELL 时有效。可选值为 SINGLE_VALUE、MIDDLE_SURFACE、TOP_SURFACE、BOTTOM_SURFACE、OFFSET_FIELD 和 GLOBAL。默认值为 GLOBAL。

*offsetField*

 String，指定偏移字段的名称。此成员仅在 *elementType*=SHELL 时有效。默认值为空字符串。

*offsetValues*

 Float，指定壳截面的偏移量。此成员仅在 *elementType*=SHELL 时有效。默认值为 0.0。

*elementType*

 SymbolicConstant，指定复合铺层中元素的类型。可选值为 SHELL、CONTINUUM_SHELL 和 SOLID。默认值为 SHELL。

*symmetric*

 Boolean，指定分析是否应使铺层对称。默认值为 OFF。

**返回值**

CompositeLayup 对象。

**异常**

AbaqusException。

### 44.2.2 suppress()

此方法抑制复合铺层。

**参数**

无。

**返回值**

无

**异常**

无。

### 44.2.3 resume()

此方法恢复先前被抑制的复合铺层。

**参数**

无。

**返回值**

无

**异常**

无。

### 44.2.4 deletePlies()

此方法从复合铺层中删除所有铺层。

**参数**

无。

**返回值**

无

**异常**

无。

### 44.2.5 setValues(...)

此方法修改 CompositeLayup 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [CompositeLayup](pt01ch44pyo02.md#ker-compositelayup-compositelayup-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 44.2.6 成员

CompositeLayup 对象的成员与 [CompositeLayup](pt01ch44pyo02.md#ker-compositelayup-compositelayup-pyc) 方法的参数具有相同的名称和描述。

此外，CompositeLayup 对象具有以下成员：

*section*

 [GeometryShellSection](pt01ch46pyo12.md) 对象。

*orientation*

 [MaterialOrientation](pt01ch44pyo04.md) 对象。

*plies*

 [CompositePlyArray](pt01ch44pyo03.md) 对象，指定组成此复合铺层的铺层。

### 44.2.7 对应分析关键字

| [*SHELL SECTION*](../key/key-link.md#usb-kws-mshellsection) |
| --- |
| [*SHELL GENERAL SECTION*](../key/key-link.md#usb-kws-mshellgensect) |
| [*SOLID SECTION*](../key/key-link.md#usb-kws-msolidsection) |

