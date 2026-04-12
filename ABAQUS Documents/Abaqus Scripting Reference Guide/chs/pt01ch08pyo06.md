# 8.6 HexagonalProfile 对象

HexagonalProfile 对象定义六角形 profile 的属性。

HexagonalProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.6.1 HexagonalProfile(...)

此方法创建一个 HexagonalProfile 对象。

**路径**

```
mdb.models[*name*].HexagonalProfile
session.odbs[*name*].HexagonalProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*r*

一个正 Float，指定六角形 profile 的 *r* 尺寸（外半径）。有关详细信息，请参阅《Abaqus Analysis User's Guide》的"Beam cross-section library," Section 29.3.9。

*t*

一个正 Float，指定六角形 profile 的 *t* 尺寸（壁厚），*t < (sqrt(3)/2)r*。

**可选参数**

无。

**返回值**

一个 HexagonalProfile 对象。

**异常**

RangeError。

### 8.6.2 setValues(...)

此方法修改 HexagonalProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [HexagonalProfile](pt01ch08pyo06.md#ker-hexagonalprofile-hexagonalprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.6.3 成员

HexagonalProfile 对象具有与 [HexagonalProfile](pt01ch08pyo06.md#ker-hexagonalprofile-hexagonalprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.6.4 对应的分析关键字

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=HEX |
| --- |
