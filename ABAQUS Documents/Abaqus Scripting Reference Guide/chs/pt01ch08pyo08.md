# 8.8 LProfile 对象

LProfile 对象定义 L 形 profile 的属性。

LProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.8.1 LProfile(...)

此方法创建一个 LProfile 对象。

**路径**

```
mdb.models[*name*].LProfile
session.odbs[*name*].LProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*a*

一个正 Float，指定 L 形 profile 的 *a* 尺寸（翼缘长度）。有关详细信息，请参阅《Abaqus Analysis User's Guide》的"Beam cross-section library," Section 29.3.9。

*b*

一个正 Float，指定 L 形 profile 的 *b* 尺寸（翼缘长度）。

*t1*

一个正 Float，指定 L 形 profile 的 *t1* 尺寸（翼缘厚度），*t1 < b*。

*t2*

一个正 Float，指定 L 形 profile 的 *t2* 尺寸（翼缘厚度），*t2 < a*。

**可选参数**

无。

**返回值**

一个 LProfile 对象。

**异常**

RangeError。

### 8.8.2 setValues(...)

此方法修改 LProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [LProfile](pt01ch08pyo08.md#ker-lprofile-lprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.8.3 成员

LProfile 对象具有与 [LProfile](pt01ch08pyo08.md#ker-lprofile-lprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.8.4 对应的分析关键字

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=L |
| --- |
