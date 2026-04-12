# 8.10 RectangularProfile 对象

RectangularProfile 对象定义实心矩形 profile 的属性。

RectangularProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.10.1 RectangularProfile(...)

此方法创建一个 RectangularProfile 对象。

**路径**

```
mdb.models[*name*].RectangularProfile
session.odbs[*name*].RectangularProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*a*

一个正 Float，指定矩形 profile 的 *a* 尺寸。有关详细信息，请参阅《Abaqus Analysis User's Guide》的"Beam cross-section library," Section 29.3.9。

*b*

一个正 Float，指定矩形 profile 的 *b* 尺寸。

**可选参数**

无。

**返回值**

一个 RectangularProfile 对象。

**异常**

RangeError。

### 8.10.2 setValues(...)

此方法修改 RectangularProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [RectangularProfile](pt01ch08pyo10.md#ker-rectangularprofile-rectangularprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.10.3 成员

RectangularProfile 对象具有与 [RectangularProfile](pt01ch08pyo10.md#ker-rectangularprofile-rectangularprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.10.4 对应的分析关键字

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=RECT |
| --- |
