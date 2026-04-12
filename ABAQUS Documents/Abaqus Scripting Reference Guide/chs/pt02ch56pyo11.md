# 56.11 SpectrumAmplitude 对象







SpectrumAmplitude 对象定义用于响应谱分析中位移、速度或加速度的响应谱。

SpectrumAmplitude 对象派生自 [Amplitude](pt02ch56pyo01.md) 对象。

**访问**

```
Api.amplitudes()[*name*]
```

### 56.11.1 SpectrumAmplitude(...)

此方法创建 SpectrumAmplitude 对象。

**路径**

```
Api.SpectrumAmplitude
```

**原型**

```
odb_SpectrumAmplitude&
SpectrumAmplitude(const odb_String& name,
                  const odb_String& method,
                  const odb_SequenceSequenceDouble& data,
                  const odb_String& specificationUnits,
                  const odb_String& eventUnits,
                  const odb_String& solution,
                  double timeIncrement,
                  double gravity,
                  bool criticalDamping,
                  const odb_String& timeSpan,
                  const odb_String& amplitude);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*method*

一个 odb_String，指定指定谱的方法。可能的值为 "DEFINE" 和 "CALCULATE"。

*data*

一个 odb_SequenceSequenceDouble，指定幅值、频率和阻尼值。

**可选参数**

*specificationUnits*

一个 odb_String，指定用于指定谱的单位。可能的值为 "DISPLACEMENT"、"VELOCITY"、"ACCELERATION" 和 "GRAVITY"。默认值为 "ACCELERATION"。

*eventUnits*

一个 odb_String，指定用于描述计算中使用的动态事件的单位。可能的值为 "EVENT_DISPLACEMENT"、"EVENT_VELOCITY"、"EVENT_ACCELERATION" 和 "EVENT_GRAVITY"。默认值为 "EVENT_ACCELERATION"。

*solution*

一个 odb_String，指定动力学方程的求解方法。可能的值为 "ABSOLUTE_VALUE" 和 "RELATIVE_VALUE"。默认值为 "ABSOLUTE_VALUE"。

*timeIncrement*

一个 Double，指定用于计算谱的隐式时间增量。当 *method* = "CALCULATE" 时需要此参数。默认值为 0.0。

*gravity*

一个 Double，指定重力加速度。当 *specificationUnits* = "GRAVITY" 或 *eventUnits* = "GRAVITY" 时仅适用此参数。默认值为 1.0。

*criticalDamping*

一个 Boolean，指定是为仅指定的临界阻尼值范围还是为值列表计算谱。如果 *criticalDamping* = true，则仅为指定的临界阻尼值范围计算谱。如果 *criticalDamping* = false，则为阻尼值列表计算谱。默认值为 false。

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

*amplitude*

一个 odb_String，指定用于计算谱的动态事件幅值的名称。默认值为空字符串。

**返回值**

SpectrumAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 56.11.2 setValues(...)

此方法修改 SpectrumAmplitude 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [SpectrumAmplitude](pt02ch56pyo11.md#ker-spectrumamplitude-spectrumamplitude-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 56.11.3 成员

SpectrumAmplitude 对象具有与 [SpectrumAmplitude](pt02ch56pyo11.md#ker-spectrumamplitude-spectrumamplitude-cpp) 方法的参数具有相同名称和描述的成员。

### 56.11.4 对应的分析关键字

| [*SPECTRUM](../key/key-link.md#usb-kws-mspectrum) |
| --- |

