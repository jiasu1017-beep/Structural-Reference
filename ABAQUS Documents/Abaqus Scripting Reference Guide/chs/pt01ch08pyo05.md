# 8.5 GeneralizedProfile 对象

GeneralizedProfile 对象通过其面积、惯性矩等定义 profile 的属性。

GeneralizedProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.5.1 GeneralizedProfile(...)

此方法创建一个 GeneralizedProfile 对象。

**路径**

```
mdb.models[*name*].GeneralizedProfile
session.odbs[*name*].GeneralizedProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*area*

一个 Float，指定 profile 的横截面积。

*i11*

一个 Float，指定关于 1 轴弯曲的惯性矩，![](../graphics/ker_eqn00019.gif)。

*i12*

一个 Float，指定交叉弯曲的惯性矩，![](../graphics/ker_eqn00020.gif)。

*i22*

一个 Float，指定关于 2 轴弯曲的惯性矩，![](../graphics/ker_eqn00021.gif)。

*j*

一个 Float，指定扭转常数，![](../graphics/ker_eqn00022.gif)。

*gammaO*

一个 Float，指定扇形矩，![](../graphics/ker_eqn00023.gif)。

*gammaW*

一个 Float，指定翘曲常数，![](../graphics/ker_eqn00024.gif)。

**可选参数**

无。

**返回值**

一个 GeneralizedProfile 对象。

**异常**

RangeError。

### 8.5.2 setValues(...)

此方法修改 GeneralizedProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [GeneralizedProfile](pt01ch08pyo05.md#ker-generalizedprofile-generalizedprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.5.3 成员

GeneralizedProfile 对象具有与 [GeneralizedProfile](pt01ch08pyo05.md#ker-generalizedprofile-generalizedprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.5.4 对应的分析关键字

| [*BEAM GENERAL SECTION](../key/key-link.md#usb-kws-mbeamgensect), SECTION=GENERAL or NONLINEAR GENERAL |
| --- |
