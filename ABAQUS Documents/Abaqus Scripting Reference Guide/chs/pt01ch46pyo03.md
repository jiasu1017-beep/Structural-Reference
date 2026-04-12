# 46.3 AcousticInterfaceSection 对象

AcousticInterfaceSection 对象定义声学截面的属性。

AcousticInterfaceSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.3.1 AcousticInterfaceSection(...)

此方法创建 AcousticInterfaceSection 对象。

**Path**

```
mdb.models[*name*].AcousticInterfaceSection
session.odbs[*name*].AcousticInterfaceSection
```

**必需参数**

*name*

 String，指定存储库键。

**可选参数**

*thickness*

 Float，指定截面厚度。可能的值为 *thickness* ![](../graphics/ker_eqn00060.gif) 0.0。默认值为 1.0。

**返回值**

AcousticInterfaceSection 对象。

**异常**

InvalidNameError 和 RangeError。

### 46.3.2 setValues(...)

此方法修改 AcousticInterfaceSection 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [AcousticInterfaceSection](pt01ch46pyo03.md#ker-acousticinterfacesection-acousticinterfacesection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 46.3.3 成员

AcousticInterfaceSection 对象的成员与 [AcousticInterfaceSection](pt01ch46pyo03.md#ker-acousticinterfacesection-acousticinterfacesection-pyc) 方法的参数具有相同的名称和描述。

### 46.3.4 对应分析关键字

| [*INTERFACE*](../key/key-link.md#usb-kws-minterface) |
| --- |

