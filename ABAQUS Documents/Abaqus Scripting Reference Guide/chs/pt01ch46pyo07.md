# 46.7 CompositeSolidSection 对象

CompositeSolidSection 对象定义复合实体截面的属性。

CompositeSolidSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.7.1 CompositeSolidSection(...)

此方法创建 CompositeSolidSection 对象。

**Path**

```
mdb.models[*name*].CompositeSolidSection
session.odbs[*name*].CompositeSolidSection
```

**必需参数**

*name*

 String，指定存储库键。

*layup*

 [SectionLayerArray](pt01ch46pyo20.md) 对象，指定实体截面。

**可选参数**

*symmetric*

 Boolean，指定分析是否应使铺层对称。默认值为 OFF。

*layupName*

 String，指定此截面的铺层名称。默认值为空字符串。

**返回值**

CompositeSolidSection 对象。

**异常**

无。

### 46.7.2 setValues(...)

此方法修改 CompositeSolidSection 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [CompositeSolidSection](pt01ch46pyo07.md#ker-compositesolidsection-compositesolidsection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 46.7.3 成员

CompositeSolidSection 对象的成员与 [CompositeSolidSection](pt01ch46pyo07.md#ker-compositesolidsection-compositesolidsection-pyc) 方法的参数具有相同的名称和描述。

### 46.7.4 对应分析关键字

| [*SOLID SECTION*](../key/key-link.md#usb-kws-msolidsection) |
| --- |

