# 8.4 CircularProfile 对象

CircularProfile 对象定义实心圆 profile 的属性。

CircularProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.4.1 CircularProfile(...)

此方法创建一个 CircularProfile 对象。

**路径**

```
mdb.models[*name*].CircularProfile
session.odbs[*name*].CircularProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*r*

一个正 Float，指定圆 profile 的 *r* 尺寸（外半径）。有关详细信息，请参阅《Abaqus Analysis User's Guide》的"Beam cross-section library," Section 29.3.9。

**可选参数**

无。

**返回值**

一个 CircularProfile 对象。

**异常**

RangeError。

### 8.4.2 setValues(...)

此方法修改 CircularProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CircularProfile](pt01ch08pyo04.md#ker-circularprofile-circularprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.4.3 成员

CircularProfile 对象具有与 [CircularProfile](pt01ch08pyo04.md#ker-circularprofile-circularprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.4.4 对应的分析关键字

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=CIRC |
| --- |
