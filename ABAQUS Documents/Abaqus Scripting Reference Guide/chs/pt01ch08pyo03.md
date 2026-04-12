# 8.3 BoxProfile 对象

BoxProfile 对象定义箱形 profile 的属性。

BoxProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.3.1 BoxProfile(...)

此方法创建一个 BoxProfile 对象。

**路径**

```
mdb.models[*name*].BoxProfile
session.odbs[*name*].BoxProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*a*

一个 Float，指定箱形 profile 的 *a* 尺寸。有关详细信息，请参阅《Abaqus Analysis User's Guide》的"Beam cross-section library," Section 29.3.9。

*b*

一个 Float，指定箱形 profile 的 *b* 尺寸。

*uniformThickness*

一个 Boolean，指定厚度是否均匀。

*t1*

一个 Float，指定均匀壁厚（如果 *uniformThickness*=ON），或者第一段壁厚（如果 *uniformThickness*=OFF）。

**可选参数**

*t2*

一个 Float，指定第二段壁厚。*t2* 仅在 *uniformThickness*=OFF 时需要。默认值为 0.0。

*t3*

一个 Float，指定第三段壁厚。*t3* 仅在 *uniformThickness*=OFF 时需要。默认值为 0.0。

*t4*

一个 Float，指定第四段壁厚。*t4* 仅在 *uniformThickness*=OFF 时需要。默认值为 0.0。

**返回值**

一个 BoxProfile 对象。

**异常**

RangeError。

### 8.3.2 setValues(...)

此方法修改 BoxProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BoxProfile](pt01ch08pyo03.md#ker-boxprofile-boxprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.3.3 成员

BoxProfile 对象具有与 [BoxProfile](pt01ch08pyo03.md#ker-boxprofile-boxprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.3.4 对应的分析关键字

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=BOX |
| --- |
