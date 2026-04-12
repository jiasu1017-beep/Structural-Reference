# 3.7 ModulatedAmplitude 对象





ModulatedAmplitude 对象定义一个调制幅度曲线。

ModulatedAmplitude 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.7.1 ModulatedAmplitude(...)

此方法创建一个 ModulatedAmplitude 对象。

**路径**

```
mdb.models[*name*].ModulatedAmplitude
session.odbs[*name*].ModulatedAmplitude
```

**必需参数**

*name*

一个 String，指定仓库键。

*initial*

一个 Float，指定常数 ![](../graphics/ker_eqn00009.gif)。

*magnitude*

一个 Float，指定系数 ![](../graphics/ker_eqn00010.gif)。

*start*

一个 Float，指定开始时间 ![](../graphics/ker_eqn00011.gif)。可能的值为非负数。

*frequency1*

一个 Float，指定圆频率 1 (![](../graphics/ker_eqn00014.gif))。可能的值为正数。

*frequency2*

一个 Float，指定圆频率 2 (![](../graphics/ker_eqn00015.gif))。可能的值为正数。

**可选参数**

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。

**返回值**

一个 ModulatedAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 3.7.2 setValues(...)

此方法修改 ModulatedAmplitude 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ModulatedAmplitude](pt01ch03pyo07.md#ker-modulatedamplitude-modulatedamplitude-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 3.7.3 成员

ModulatedAmplitude 对象具有与 [ModulatedAmplitude](pt01ch03pyo07.md#ker-modulatedamplitude-modulatedamplitude-pyc) 方法参数相同名称和描述的成员。

### 3.7.4 对应分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |



