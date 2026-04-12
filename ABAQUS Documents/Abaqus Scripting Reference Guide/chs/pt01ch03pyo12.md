# 3.12 SpectrumAmplitude 对象





SpectrumAmplitude 对象定义用于响应谱分析中位移、速度或加速度的响应谱。

SpectrumAmplitude 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.12.1 SpectrumAmplitude(...)

此方法创建一个 SpectrumAmplitude 对象。

**路径**

```
mdb.models[*name*].SpectrumAmplitude
session.odbs[*name*].SpectrumAmplitude
```

**必需参数**

*name*

一个 String，指定仓库键。

*method*

一个 SymbolicConstant，指定指定谱的方法。可能的值为 DEFINE 和 CALCULATE。

*data*

一个 Float 序列的序列，指定幅值、频率和阻尼值。

**可选参数**

*specificationUnits*

一个 SymbolicConstant，指定用于指定谱的单位。可能的值为 DISPLACEMENT、VELOCITY、ACCELERATION 和 GRAVITY。默认值为 ACCELERATION。

*eventUnits*

一个 SymbolicConstant，指定用于描述计算中使用的幅度中动态事件的单位。可能的值为 EVENT_DISPLACEMENT、EVENT_VELOCITY、EVENT_ACCELERATION 和 EVENT_GRAVITY。默认值为 EVENT_ACCELERATION。

*solution*

一个 SymbolicConstant，指定动态方程的求解方法。可能的值为 ABSOLUTE_VALUE 和 RELATIVE_VALUE。默认值为 ABSOLUTE_VALUE。

*timeIncrement*

一个 Float，指定用于计算谱的隐式时间增量。当 *method* = CALCULATE 时需要此参数。默认值为 0.0。

*gravity*

一个 Float，指定重力加速度。当 *specificationUnits* = GRAVITY 或 *eventUnits* = GRAVITY 时仅适用此参数。默认值为 1.0。

*criticalDamping*

一个 Boolean，指定仅为指定范围的临界阻尼值还是为一系列值计算谱。如果 *criticalDamping* = ON，则仅为指定范围的临界阻尼值计算谱。如果 *criticalDamping* = OFF，则为一系列阻尼值计算谱。默认值为 OFF。

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。

*amplitude*

一个 String，指定用于计算谱的动态事件的幅度名称。默认值为空字符串。

**返回值**

一个 SpectrumAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 3.12.2 setValues(...)

此方法修改 SpectrumAmplitude 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SpectrumAmplitude](pt01ch03pyo12.md#ker-spectrumamplitude-spectrumamplitude-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 3.12.3 成员

SpectrumAmplitude 对象具有与 [SpectrumAmplitude](pt01ch03pyo12.md#ker-spectrumamplitude-spectrumamplitude-pyc) 方法参数相同名称和描述的成员。

### 3.12.4 对应分析关键字

| [*SPECTRUM](../key/key-link.md#usb-kws-mspectrum) |
| --- |



