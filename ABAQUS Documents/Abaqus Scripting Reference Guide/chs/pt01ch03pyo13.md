# 3.13 TabularAmplitude 对象





TabularAmplitude 对象定义为时间刻度上方便点处的值表的幅度曲线。

TabularAmplitude 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.13.1 TabularAmplitude(...)

此方法创建一个 TabularAmplitude 对象。

**路径**

```
mdb.models[*name*].TabularAmplitude
session.odbs[*name*].TabularAmplitude
```

**必需参数**

*name*

一个 String，指定仓库键。

*data*

一个 Float 对序列，指定时间/频率和幅度对。时间/频率的可能值为正数。

**可选参数**

*smooth*

SymbolicConstant SOLVER_DEFAULT 或一个 Float，指定平滑程度。可能的 Float 值为 0 到 0.5 之间。如果 *smooth*=SOLVER_DEFAULT，则由求解器确定默认平滑程度。默认值为 SOLVER_DEFAULT。

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。

**返回值**

一个 TabularAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 3.13.2 setValues(...)

此方法修改 TabularAmplitude 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [TabularAmplitude](pt01ch03pyo13.md#ker-tabularamplitude-tabularamplitude-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 3.13.3 成员

TabularAmplitude 对象具有与 [TabularAmplitude](pt01ch03pyo13.md#ker-tabularamplitude-tabularamplitude-pyc) 方法参数相同名称和描述的成员。

此外，TabularAmplitude 对象可以具有以下成员：

*baselineCorrection*

一个 [BaselineCorrection](pt01ch03pyo03.md) 对象。

### 3.13.4 对应分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |



