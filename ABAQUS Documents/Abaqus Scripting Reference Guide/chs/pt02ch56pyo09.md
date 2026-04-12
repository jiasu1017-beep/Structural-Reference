# 56.9 SmoothStepAmplitude 对象







SmoothStepAmplitude 对象定义从一个数据点到另一个数据点平滑上升或下降的幅值。

SmoothStepAmplitude 对象派生自 [Amplitude](pt02ch56pyo01.md) 对象。

**访问**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.9.1 SmoothStepAmplitude(...)

此方法创建 SmoothStepAmplitude 对象。

**路径**

```
amplitudeApi.SmoothStepAmplitude
```

**原型**

```
odb_SmoothStepAmplitude&
SmoothStepAmplitude(const odb_String& name,
                    const odb_SequenceSequenceDouble& data,
                    const odb_String& timeSpan);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*data*

一个 odb_SequenceSequenceDouble，指定时间/频率和幅值对。时间/频率的可能值为正数。

**可选参数**

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

**返回值**

SmoothStepAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 56.9.2 setValues(...)

此方法修改 SmoothStepAmplitude 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [SmoothStepAmplitude](pt02ch56pyo09.md#ker-smoothstepamplitude-smoothstepamplitude-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 56.9.3 成员

SmoothStepAmplitude 对象具有与 [SmoothStepAmplitude](pt02ch56pyo09.md#ker-smoothstepamplitude-smoothstepamplitude-cpp) 方法的参数具有相同名称和描述的成员。

### 56.9.4 对应的分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |

