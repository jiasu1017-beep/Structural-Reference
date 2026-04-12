# 8.12 TrapezoidalProfile 对象

TrapezoidalProfile 对象定义梯形 profile 的属性。

TrapezoidalProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.12.1 TrapezoidalProfile(...)

此方法创建一个 TrapezoidalProfile 对象。

**路径**

```
mdb.models[*name*].TrapezoidalProfile
session.odbs[*name*].TrapezoidalProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*a*

一个正 Float，指定梯形 profile 的 *a* 尺寸。有关详细信息，请参阅《Abaqus Analysis User's Guide》的"Beam cross-section library," Section 29.3.9。

*b*

一个正 Float，指定梯形 profile 的 *b* 尺寸。

*c*

一个正 Float，指定梯形 profile 的 *c* 尺寸。

*d*

一个 Float，指定梯形 profile 的 *d* 尺寸。

**可选参数**

无。

**返回值**

一个 TrapezoidalProfile 对象。

**异常**

RangeError。

### 8.12.2 setValues(...)

此方法修改 TrapezoidalProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [TrapezoidalProfile](pt01ch08pyo12.md#ker-trapezoidalprofile-trapezoidalprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.12.3 成员

TrapezoidalProfile 对象具有与 [TrapezoidalProfile](pt01ch08pyo12.md#ker-trapezoidalprofile-trapezoidalprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.12.4 对应的分析关键字

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=TRAPEZOID |
| --- |
