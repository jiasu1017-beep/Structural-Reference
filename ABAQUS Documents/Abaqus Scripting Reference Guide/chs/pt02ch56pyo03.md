# 56.4 DecayAmplitude 对象







DecayAmplitude 对象使用指数衰减定义幅值曲线。

DecayAmplitude 对象派生自 [Amplitude](pt02ch56pyo01.md) 对象。

**访问**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.4.1 DecayAmplitude(...)

此方法创建 DecayAmplitude 对象。

**路径**

```
amplitudeApi.DecayAmplitude
```

**原型**

```
odb_DecayAmplitude&
DecayAmplitude(const odb_String& name,
               double initial,
               double maximum,
               double start,
               double decayTime,
               const odb_String& timeSpan);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*initial*

一个 Double，指定常数 ![](../graphics/ker_eqn00009.gif)。

*maximum*

一个 Double，指定系数 ![](../graphics/ker_eqn00010.gif)。

*start*

一个 Double，指定起始时间 ![](../graphics/ker_eqn00011.gif)。可能的值为非负数。

*decayTime*

一个 Double，指定衰减时间 ![](../graphics/ker_eqn00012.gif)。可能的值为非负数。

**可选参数**

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

**返回值**

DecayAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 56.4.2 setValues(...)

此方法修改 DecayAmplitude 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [DecayAmplitude](pt02ch56pyo04.md#ker-decayamplitude-decayamplitude-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 56.4.3 成员

DecayAmplitude 对象具有与 [DecayAmplitude](pt02ch56pyo04.md#ker-decayamplitude-decayamplitude-cpp) 方法的参数具有相同名称和描述的成员。

### 56.4.4 对应的分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |

