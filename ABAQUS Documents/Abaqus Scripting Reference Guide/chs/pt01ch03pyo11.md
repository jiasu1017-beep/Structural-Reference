# 3.11 SolutionDependentAmplitude 对象





SolutionDependentAmplitude 对象定义用于超塑成形分析的对解相依幅度。

SolutionDependentAmplitude 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.11.1 SolutionDependentAmplitude(...)

此方法创建一个 SolutionDependentAmplitude 对象。

**路径**

```
mdb.models[*name*].SolutionDependentAmplitude
session.odbs[*name*].SolutionDependentAmplitude
```

**必需参数**

*name*

一个 String，指定仓库键。

**可选参数**

*initial*

一个 Float，指定初始幅度值。可能的值在 *minimum* 和 *maximum* 之间。默认值为 1.0。

*minimum*

一个 Float，指定最小幅度值。可能的值小于 *maximum* 和 *initial*。默认值为 0.1。

*maximum*

一个 Float，指定最大幅度值。可能的值大于 *minimum* 和 *initial*。默认值为 1000.0。

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。

**返回值**

一个 SolutionDependentAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 3.11.2 setValues(...)

此方法修改 SolutionDependentAmplitude 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SolutionDependentAmplitude](pt01ch03pyo11.md#ker-solutiondependentamplitude-solutiondependentamplitud-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 3.11.3 成员

SolutionDependentAmplitude 对象具有与 [SolutionDependentAmplitude](pt01ch03pyo11.md#ker-solutiondependentamplitude-solutiondependentamplitud-pyc) 方法参数相同名称和描述的成员。

### 3.11.4 对应分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |



