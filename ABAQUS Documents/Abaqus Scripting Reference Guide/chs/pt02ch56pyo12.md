# 56.12 TabularAmplitude 对象







TabularAmplitude 对象定义为方便点在时间尺度上的值的表的幅值曲线。

TabularAmplitude 对象派生自 [Amplitude](pt02ch56pyo01.md) 对象。

**访问**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.12.1 TabularAmplitude(...)

此方法创建 TabularAmplitude 对象。

**路径**

```
amplitudeApi.TabularAmplitude
```

**原型**

```
odb_TabularAmplitude&
TabularAmplitude(const odb_String& name,
                 const odb_SequenceSequenceDouble& data,
                 odb_Union smooth,
                 const odb_String& timeSpan);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

*data*

一个 odb_SequenceSequenceDouble，指定时间/频率和幅值对。时间/频率的可能值为正数。

**可选参数**

*smooth*

字符串 "SOLVER_DEFAULT" 或一个 Double，指定平滑度。可能的浮点值在 0 到 0.5 之间。如果 *smooth*="SOLVER_DEFAULT"，则由求解器确定默认平滑度。默认值为 "SOLVER_DEFAULT"。

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

**返回值**

TabularAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 56.12.2 setValues(...)

此方法修改 TabularAmplitude 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [TabularAmplitude](pt02ch56pyo12.md#ker-tabularamplitude-tabularamplitude-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 56.12.3 成员

TabularAmplitude 对象具有与 [TabularAmplitude](pt02ch56pyo12.md#ker-tabularamplitude-tabularamplitude-cpp) 方法的参数具有相同名称和描述的成员。

此外，TabularAmplitude 对象可以具有以下成员：

**原型**

```
odb_BaselineCorrection baselineCorrection() const;
```

*baselineCorrection*

一个 [BaselineCorrection](pt02ch56pyo03.md) 对象。

### 56.12.4 对应的分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |

