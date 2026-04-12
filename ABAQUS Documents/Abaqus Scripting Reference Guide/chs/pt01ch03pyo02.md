# 3.2 ActuatorAmplitude 对象





ActuatorAmplitude 对象定义一个致动器幅度曲线。

ActuatorAmplitude 对象派生自 [Amplitude](pt01ch03pyo01.md) 对象。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*]
import odbAmplitude
session.odbs[*name*].amplitudes[*name*]
```

### 3.2.1 ActuatorAmplitude(...)

此方法创建一个 ActuatorAmplitude 对象。

**路径**

```
mdb.models[*name*].ActuatorAmplitude
session.odbs[*name*].ActuatorAmplitude
```

**必需参数**

*name*

一个 String，指定仓库键。

**可选参数**

*timeSpan*

一个 SymbolicConstant，指定幅度的时间跨度。可能的值为 STEP 和 TOTAL。默认值为 STEP。

**返回值**

一个 ActuatorAmplitude 对象。

**异常**

InvalidNameError 和 RangeError。

### 3.2.2 setValues(...)

此方法修改 ActuatorAmplitude 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ActuatorAmplitude](pt01ch03pyo02.md#ker-actuatoramplitude-actuatoramplitude-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 3.2.3 成员

ActuatorAmplitude 对象具有与 [ActuatorAmplitude](pt01ch03pyo02.md#ker-actuatoramplitude-actuatoramplitude-pyc) 方法参数相同名称和描述的成员。

### 3.2.4 对应分析关键字

| [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
| --- |



