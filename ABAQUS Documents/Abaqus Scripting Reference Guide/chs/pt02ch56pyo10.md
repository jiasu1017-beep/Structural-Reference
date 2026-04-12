# 56.10 SolutionDependentAmplitude 对象







SolutionDependentAmplitude 对象定义超塑性成形分析的解相关幅值。

SolutionDependentAmplitude 对象派生自 [Amplitude](pt02ch56pyo01.md) 对象。

**访问**

```
amplitudeApi.amplitudes()[*name*]
```

### 56.10.1 SolutionDependentAmplitude(...)

此方法创建 SolutionDependentAmplitude 对象。

**路径**

```
amplitudeApi.SolutionDependentAmplitude
```

**原型**

```
odb_SolutionDependentAmplitude&
SolutionDependentAmplitude(const odb_String& name,
                           double initial,
                           double minimum,
                           double maximum,
                           const odb_String& timeSpan);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。

**可选参数**

*initial*

一个 Double，指定初始幅值。可能的值为介于 *minimum* 和 *maximum* 之间的值。默认值为 1.0。

*minimum*

一个 Double，指定最小幅值。可能的值小于 *maximum* 和 *initial*。默认值为 0.1。

*maximum*

一个 Double，指定最大幅值。可能的值大于 *minimum* 和 *initial*。默认值为 1000.0。

*timeSpan*

一个 odb_String，指定幅值的时间跨度。可能的值为 "STEP" 和 "TOTAL"。默认值为 "STEP"。

**返回值**

SolutionDependentAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 56.10.2 setValues(...)

此方法修改 SolutionDependentAmplitude 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [SolutionDependentAmplitude](pt02ch56pyo10.md#ker-solutiondependentamplitude-solutiondependentamplitud-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 56.10.3 成员

SolutionDependentAmplitude 对象具有与 [SolutionDependentAmplitude](pt02ch56pyo10.md#ker-solutiondependentamplitude-solutiondependentamplitud-cpp) 方法的参数具有相同名称和描述的成员。

### 56.10.4 对应的分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |

