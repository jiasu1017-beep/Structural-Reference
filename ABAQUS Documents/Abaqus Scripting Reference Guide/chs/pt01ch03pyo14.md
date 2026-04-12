# 3.14 UserAmplitude 对象





UserAmplitude 对象使用 [`UAMP`](../sub/sub-link.md#sub-xsl-uamp) 或 [`VUAMP`](../sub/sub-link.md#sub-xsl-vuamp) 用户子程序定义幅度曲线。

UserAmplitude 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.14.1 UserAmplitude(...)

此方法创建一个 UserAmplitude 对象。

**路径**

```
mdb.models[*name*].UserAmplitude
session.odbs[*name*].UserAmplitude
```

**必需参数**

*name*

一个 String，指定仓库键。

*numVariables*

一个 Int，指定 [`UAMP`](../sub/sub-link.md#sub-xsl-uamp) 或 [`VUAMP`](../sub/sub-link.md#sub-xsl-vuamp) 用户子程序的变量数。

**可选参数**

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。

**返回值**

一个 UserAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 3.14.2 setValues(...)

此方法修改 UserAmplitude 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [UserAmplitude](pt01ch03pyo14.md#ker-useramplitude-useramplitude-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 3.14.3 成员

UserAmplitude 对象具有与 [UserAmplitude](pt01ch03pyo14.md#ker-useramplitude-useramplitude-pyc) 方法参数相同名称和描述的成员。

### 3.14.4 对应分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |



