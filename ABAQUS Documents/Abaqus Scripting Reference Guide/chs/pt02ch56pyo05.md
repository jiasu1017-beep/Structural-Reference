# 56.5 EquallySpacedAmplitude 对象







EquallySpacedAmplitude 对象定义在指定时间值开始的固定时间间隔的幅值列表。

EquallySpacedAmplitude 对象派生自 [Amplitude](pt02ch56pyo01.md) 对象。

**访问**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.5.1 EquallySpacedAmplitude(...)

此方法创建 EquallySpacedAmplitude 对象。

**路径**

```
amplitudeApi.EquallySpacedAmplitude
```

**原型**

```
odb_EquallySpacedAmplitude&
EquallySpacedAmplitude(const odb_String& name,
                       double fixedInterval,
                       const odb_SequenceDouble& data,
                       double begin,
                       odb_Union smooth,
                       const odb_String& timeSpan);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*fixedInterval*

一个 Double，指定给出幅值数据的固定时间间隔。可能的值为正数。

*data*

一个 odb_SequenceDouble，指定幅值。

**可选参数**

*begin*

一个 Double，指定给出第一个幅值数据的时间。可能的值为非负数。默认值为 0.0。

*smooth*

字符串 "SOLVER_DEFAULT" 或一个 Double，指定平滑度。可能的浮点值为 0 ![](../graphics/ker_eqn00013.gif) *smoothing* ![](../graphics/ker_eqn00013.gif) 0.5。如果 *smooth*="SOLVER_DEFAULT"，则由求解器确定默认平滑度。默认值为 "SOLVER_DEFAULT"。

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

**返回值**

EquallySpacedAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 56.5.2 setValues(...)

此方法修改 EquallySpacedAmplitude 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [EquallySpacedAmplitude](pt02ch56pyo05.md#ker-equallyspacedamplitude-equallyspacedamplitude-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 56.5.3 成员

EquallySpacedAmplitude 对象具有与 [EquallySpacedAmplitude](pt02ch56pyo05.md#ker-equallyspacedamplitude-equallyspacedamplitude-cpp) 方法的参数具有相同名称和描述的成员。

此外，EquallySpacedAmplitude 对象可以具有以下成员：

**原型**

```
odb_BaselineCorrection baselineCorrection() const;
```

*baselineCorrection*

一个 [BaselineCorrection](pt02ch56pyo03.md) 对象。

### 56.5.4 对应的分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |

