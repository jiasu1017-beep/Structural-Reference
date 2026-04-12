# 51.7 Monitor 对象

Monitor 对象用于定义要监控的自由度。

**访问**

```
import step
mdb.models[*name*].steps[*name*].monitor
```

### 51.7.1 Monitor(...)

此方法创建在通用或模态过程中监控自由度的请求。

**路径**

```
mdb.models[*name*].steps[*name*].Monitor
```

**必要参数**

*node*

一个 String，指定要监控的区域名称。

*dof*

一个 SymbolicConstant，指定要在节点处监控的自由度。可选值为：
- U1
- U2
- U3
- UR1
- UR2
- UR3
- WARP
- FLUID_PRESSURE
- ELECTRICAL_POTENTIAL
- NT11
- NT30
- NN11
- NN30

NT 标识符不适用于质量扩散。NN 标识符仅适用于质量扩散。

*frequency*

一个 Int，指定输出频率（以增量计）。此参数仅对 Abaqus/Standard 分析有效。

**可选参数**

无。

**返回的值**

一个 Monitor 对象。

**异常**

RangeError。

### 51.7.2 setValues(...)

此方法修改 Monitor 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [Monitor](pt01ch51pyo07.md#ker-monitor-monitor-pyc) 方法的参数相同。

**返回的值**

无。

**异常**

RangeError。

### 51.7.3 成员

Monitor 对象的成员与 [Monitor](pt01ch51pyo07.md#ker-monitor-monitor-pyc) 方法的参数具有相同的名称和描述。

### 51.7.4 对应的分析关键字

| [*MONITOR](../key/key-link.md#usb-kws-hmonitor) |
| --- |
