# 8.7 IProfile 对象

IProfile 对象定义 I 形 profile 的属性。

IProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.7.1 IProfile(...)

此方法创建一个 IProfile 对象。

**路径**

```
mdb.models[*name*].IProfile
session.odbs[*name*].IProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*l*

一个 Float，指定 I 形 profile 的 *l* 尺寸（从下翼缘表面到 1 轴的偏移量）。有关详细信息，请参阅《Abaqus Analysis User's Guide》的"Beam cross-section library," Section 29.3.9。

*h*

一个 Float，指定 I 形 profile 的 *h* 尺寸（高度）。

*b1*

一个 Float，指定 I 形 profile 的 *b1* 尺寸（下翼缘宽度）。

*b2*

一个 Float，指定 I 形 profile 的 *b2* 尺寸（上翼缘宽度）。

*t1*

一个 Float，指定 I 形 profile 的 *t1* 尺寸（下翼缘厚度）。

*t2*

一个 Float，指定 I 形 profile 的 *t2* 尺寸（上翼缘厚度）。

*t3*

一个 Float，指定 I 形 profile 的 *t3* 尺寸（腹板厚度）。

**可选参数**

无。

**返回值**

一个 IProfile 对象。

**异常**

RangeError。

### 8.7.2 setValues(...)

此方法修改 IProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [IProfile](pt01ch08pyo07.md#ker-iprofile-iprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.7.3 成员

IProfile 对象具有与 [IProfile](pt01ch08pyo07.md#ker-iprofile-iprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.7.4 对应的分析关键字

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=I |
| --- |
