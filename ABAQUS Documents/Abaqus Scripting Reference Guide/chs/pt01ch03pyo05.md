# 3.5 DecayAmplitude 对象





DecayAmplitude 对象使用指数衰减定义幅度曲线。

DecayAmplitude 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.5.1 DecayAmplitude(...)

此方法创建一个 DecayAmplitude 对象。

**路径**

```
mdb.models[*name*].DecayAmplitude
session.odbs[*name*].DecayAmplitude
```

**必需参数**

*name*

一个 String，指定仓库键。

*initial*

一个 Float，指定常数 ![](../graphics/ker_eqn00009.gif)。

*maximum*

一个 Float，指定系数 ![](../graphics/ker_eqn00010.gif)。

*start*

一个 Float，指定开始时间 ![](../graphics/ker_eqn00011.gif)。可能的值为非负数。

*decayTime*

一个 Float，指定衰减时间 ![](../graphics/ker_eqn00012.gif)。可能的值为非负数。

**可选参数**

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。

**返回值**

一个 DecayAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 3.5.2 setValues(...)

此方法修改 DecayAmplitude 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DecayAmplitude](pt01ch03pyo05.md#ker-decayamplitude-decayamplitude-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 3.5.3 成员

DecayAmplitude 对象具有与 [DecayAmplitude](pt01ch03pyo05.md#ker-decayamplitude-decayamplitude-pyc) 方法参数相同名称和描述的成员。

### 3.5.4 对应分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |



