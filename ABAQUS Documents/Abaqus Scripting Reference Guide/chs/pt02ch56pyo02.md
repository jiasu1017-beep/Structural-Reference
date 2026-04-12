# 56.2 ActuatorAmplitude 对象







ActuatorAmplitude 对象定义致动器幅值曲线。

ActuatorAmplitude 对象派生自 [Amplitude](pt02ch56pyo01.md) 对象。

**访问**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.2.1 ActuatorAmplitude(...)

此方法创建 ActuatorAmplitude 对象。

**路径**

```
amplitudeApi.ActuatorAmplitude
```

**原型**

```
odb_ActuatorAmplitude&
ActuatorAmplitude(const odb_String& name,
                  const odb_String& timeSpan);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

**可选参数**

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

**返回值**

ActuatorAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 56.2.2 setValues(...)

此方法修改 ActuatorAmplitude 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [ActuatorAmplitude](pt02ch56pyo02.md#ker-actuatoramplitude-actuatoramplitude-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 56.2.3 成员

ActuatorAmplitude 对象具有与 [ActuatorAmplitude](pt02ch56pyo02.md#ker-actuatoramplitude-actuatoramplitude-cpp) 方法的参数具有相同名称和描述的成员。

### 56.2.4 对应的分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |

