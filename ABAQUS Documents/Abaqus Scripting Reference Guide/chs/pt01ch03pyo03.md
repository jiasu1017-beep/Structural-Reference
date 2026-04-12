# 3.3 BaselineCorrection 对象





BaselineCorrection 对象修改加速度历史记录，以最小化从给定加速度的时间积分获得的位移的整体漂移。

**访问**

```
import amplitude
mdb.models[*name*].amplitudes[*name*].baselineCorrection
import odbAmplitude
session.odbs[*name*].amplitudes[*name*].baselineCorrection
```

### 3.3.1 BaselineCorrection(...)

此方法创建一个 BaselineCorrection 对象。

**路径**

```
mdb.models[*name*].amplitudes[*name*].BaselineCorrection
session.odbs[*name*].amplitudes[*name*].BaselineCorrection
```

**必需参数**

无。

**可选参数**

*intervals*

一个 Float 序列，指定校正时间间隔终点。可能的值为正且单调递增的 Float。默认值为空序列。

**返回值**

一个 BaselineCorrection 对象。

**异常**

RangeError。

### 3.3.2 setValues(...)

此方法修改 BaselineCorrection 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BaselineCorrection](pt01ch03pyo03.md#ker-baselinecorrection-baselinecorrection-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 3.3.3 成员

BaselineCorrection 对象具有与 [BaselineCorrection](pt01ch03pyo03.md#ker-baselinecorrection-baselinecorrection-pyc) 方法参数相同名称和描述的成员。

### 3.3.4 对应分析关键字

| [*BASELINE CORRECTION](../key/key-link.md#usb-kws-mbasecorrection) |
| --- |



