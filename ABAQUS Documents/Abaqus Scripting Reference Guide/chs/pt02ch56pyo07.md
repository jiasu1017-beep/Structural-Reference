# 56.7 PeriodicAmplitude 对象







PeriodicAmplitude 对象使用傅里叶级数定义幅值曲线。

PeriodicAmplitude 对象派生自 [Amplitude](pt02ch56pyo01.md) 对象。

**访问**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.7.1 PeriodicAmplitude(...)

此方法创建 PeriodicAmplitude 对象。

**路径**

```
amplitudeApi.PeriodicAmplitude
```

**原型**

```
odb_PeriodicAmplitude&
PeriodicAmplitude(const odb_String& name,
                  double frequency,
                  double start,
                  double a_0,
                  const odb_SequenceSequenceDouble& data,
                  const odb_String& timeSpan);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*frequency*

一个 Double，指定圆频率 ![](../graphics/ker_eqn00016.gif)。可能的值为正数。

*start*

一个 Double，指定起始时间 ![](../graphics/ker_eqn00011.gif)。可能的值为正数。

*a_0*

一个 Double，指定常数 ![](../graphics/ker_eqn00009.gif)。

*data*

一个 odb_SequenceSequenceDouble，指定 ![](../graphics/ker_eqn00017.gif) 和 ![](../graphics/ker_eqn00018.gif) 对。

**可选参数**

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

**返回值**

PeriodicAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 56.7.2 setValues(...)

此方法修改 PeriodicAmplitude 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [PeriodicAmplitude](pt02ch56pyo07.md#ker-periodicamplitude-periodicamplitude-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 56.7.3 成员

PeriodicAmplitude 对象具有与 [PeriodicAmplitude](pt02ch56pyo07.md#ker-periodicamplitude-periodicamplitude-cpp) 方法的参数具有相同名称和描述的成员。

### 56.7.4 对应的分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |

