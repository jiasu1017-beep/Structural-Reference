# 3.6 EquallySpacedAmplitude 对象





EquallySpacedAmplitude 对象定义从指定时间值开始以固定时间间隔的幅度值列表。

EquallySpacedAmplitude 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.6.1 EquallySpacedAmplitude(...)

此方法创建一个 EquallySpacedAmplitude 对象。

**路径**

```
mdb.models[*name*].EquallySpacedAmplitude
session.odbs[*name*].EquallySpacedAmplitude
```

**必需参数**

*name*

一个 String，指定仓库键。

*fixedInterval*

一个 Float，指定给出幅度数据的固定时间间隔。可能的值为正数。

*data*

一个 Float 序列，指定幅度值。

**可选参数**

*begin*

一个 Float，指定给出第一个幅度数据的时间。可能的值为非负数。默认值为 0.0。

*smooth*

SymbolicConstant SOLVER_DEFAULT 或一个 Float，指定平滑程度。可能的 Float 值为 0 ![](../graphics/ker_eqn00013.gif) *smoothing* ![](../graphics/ker_eqn00013.gif) 0.5。如果 *smooth*=SOLVER_DEFAULT，则由求解器确定默认平滑程度。默认值为 SOLVER_DEFAULT。

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。

**返回值**

一个 EquallySpacedAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 3.6.2 setValues(...)

此方法修改 EquallySpacedAmplitude 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [EquallySpacedAmplitude](pt01ch03pyo06.md#ker-equallyspacedamplitude-equallyspacedamplitude-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 3.6.3 成员

EquallySpacedAmplitude 对象具有与 [EquallySpacedAmplitude](pt01ch03pyo06.md#ker-equallyspacedamplitude-equallyspacedamplitude-pyc) 方法参数相同名称和描述的成员。

此外，EquallySpacedAmplitude 对象可以具有以下成员：

*baselineCorrection*

一个 [BaselineCorrection](pt01ch03pyo03.md) 对象。

### 3.6.4 对应分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |



