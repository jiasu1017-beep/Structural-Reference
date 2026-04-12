# 3.10 SmoothStepAmplitude 对象





SmoothStepAmplitude 对象定义从一个数据点平滑地上升或下降到另一个数据点的幅度。

SmoothStepAmplitude 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.10.1 SmoothStepAmplitude(...)

此方法创建一个 SmoothStepAmplitude 对象。

**路径**

```
mdb.models[*name*].SmoothStepAmplitude
session.odbs[*name*].SmoothStepAmplitude
```

**必需参数**

*name*

一个 String，指定仓库键。

*data*

一个 Float 对序列，指定时间/频率和幅度对。时间/频率的可能值为正数。

**可选参数**

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。

**返回值**

一个 SmoothStepAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 3.10.2 setValues(...)

此方法修改 SmoothStepAmplitude 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SmoothStepAmplitude](pt01ch03pyo10.md#ker-smoothstepamplitude-smoothstepamplitude-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 3.10.3 成员

SmoothStepAmplitude 对象具有与 [SmoothStepAmplitude](pt01ch03pyo10.md#ker-smoothstepamplitude-smoothstepamplitude-pyc) 方法参数相同名称和描述的成员。

### 3.10.4 对应分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |



