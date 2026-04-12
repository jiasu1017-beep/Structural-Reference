# 56.6 ModulatedAmplitude 对象







ModulatedAmplitude 对象定义调制幅值曲线。

ModulatedAmplitude 对象派生自 [Amplitude](pt02ch56pyo01.md) 对象。

**访问**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.6.1 ModulatedAmplitude(...)

此方法创建 ModulatedAmplitude 对象。

**路径**

```
amplitudeApi.ModulatedAmplitude
```

**原型**

```
odb_ModulatedAmplitude&
ModulatedAmplitude(const odb_String& name,
                   double initial,
                   double magnitude,
                   double start,
                   double frequency1,
                   double frequency2,
                   const odb_String& timeSpan);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*initial*

一个 Double，指定常数 ![](../graphics/ker_eqn00009.gif)。

*magnitude*

一个 Double，指定系数 ![](../graphics/ker_eqn00010.gif)。

*start*

一个 Double，指定起始时间 ![](../graphics/ker_eqn00011.gif)。可能的值为非负数。

*frequency1*

一个 Double，指定圆频率 1 (![](../graphics/ker_eqn00014.gif))。可能的值为正数。

*frequency2*

一个 Double，指定圆频率 2 (![](../graphics/ker_eqn00015.gif))。可能的值为正数。

**可选参数**

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

**返回值**

ModulatedAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 56.6.2 setValues(...)

此方法修改 ModulatedAmplitude 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [ModulatedAmplitude](pt02ch56pyo06.md#ker-modulatedamplitude-modulatedamplitude-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 56.6.3 成员

ModulatedAmplitude 对象具有与 [ModulatedAmplitude](pt02ch56pyo06.md#ker-modulatedamplitude-modulatedamplitude-cpp) 方法的参数具有相同名称和描述的成员。

### 56.6.4 对应的分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |

