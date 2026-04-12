# 56.3 BaselineCorrection 对象







BaselineCorrection 对象修改加速度历史记录，以最小化从给定加速度的时间积分获得的位移的整体漂移。

**访问**

```
amplitudeApi.amplitudes()[*name*].baselineCorrection()
```

### 56.3.1 BaselineCorrection(...)

此方法创建 BaselineCorrection 对象。

**路径**

```
amplitudeApi.amplitudes()[*name*].BaselineCorrection
```

**原型**

```
odb_BaselineCorrection&
BaselineCorrection(const odb_SequenceDouble& intervals);
```

**必需参数**

None。

**可选参数**

*intervals*

一个 odb_SequenceDouble，指定校正时间间隔端点。可能的值为正且单调递增的 Float。默认值为空序列。

**返回值**

BaselineCorrection 对象。

**异常**

RangeError。

### 56.3.2 setValues(...)

此方法修改 BaselineCorrection 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [BaselineCorrection](pt02ch56pyo03.md#ker-baselinecorrection-baselinecorrection-cpp) 方法的参数相同。

**返回值**

None

**异常**

RangeError。

### 56.3.3 成员

BaselineCorrection 对象具有与 [BaselineCorrection](pt02ch56pyo03.md#ker-baselinecorrection-baselinecorrection-cpp) 方法的参数具有相同名称和描述的成员。

### 56.3.4 对应的分析关键字

| [*BASELINE CORRECTION](../key/key-link.md#usb-kws-mbasecorrection) |
| --- |

