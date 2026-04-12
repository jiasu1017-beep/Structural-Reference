# 8.11 TProfile 对象

TProfile 对象定义 T 形 profile 的属性。

TProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.11.1 TProfile(...)

此方法创建一个 TProfile 对象。

**路径**

```
mdb.models[*name*].TProfile
session.odbs[*name*].TProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*b*

一个正 Float，指定 T 形 profile 的 *b* 尺寸（翼缘宽度）。有关详细信息，请参阅《Abaqus Analysis User's Guide》的"Beam cross-section library," Section 29.3.9。

*h*

一个正 Float，指定 T 形 profile 的 *h* 尺寸（高度）。

*l*

一个正 Float，指定 T 形 profile 的 *l* 尺寸（从腹板边缘到 1 轴的偏移量）。

*tf*

一个正 Float，指定 T 形 profile 的 *tf* 尺寸（翼缘厚度），*tf < h*。

*tw*

一个正 Float，指定 T 形 profile 的 *tw* 尺寸（腹板厚度），*tw < b*。

**可选参数**

无。

**返回值**

一个 TProfile 对象。

**异常**

RangeError。

### 8.11.2 setValues(...)

此方法修改 TProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [TProfile](pt01ch08pyo11.md#ker-tprofile-tprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.11.3 成员

TProfile 对象具有与 [TProfile](pt01ch08pyo11.md#ker-tprofile-tprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.11.4 对应的分析关键字

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=I |
| --- |
