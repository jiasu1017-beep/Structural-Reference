# 51.9 TimePoint 对象

TimePoint 对象定义将数据写入输出数据库或重启文件的时间点。

**访问**

```
import step
mdb.models[*name*].timePoints[*name*]
```

### 51.9.1 TimePoint(...)

此方法创建一个 TimePoint 对象。

**路径**

```
mdb.models[*name*].TimePoint
```

**必要参数**

*name*

一个 String，指定仓库键。

*points*

一个 Float 序列的序列，指定将数据写入输出数据库或重启文件的时间点。

**可选参数**

无。

**返回的值**

一个 TimePoint 对象。

**异常**

InvalidNameError 和 RangeError。

### 51.9.2 setValues(...)

此方法修改 TimePoint 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [TimePoint](pt01ch51pyo09.md#ker-timepoint-timepoint-pyc) 方法的参数相同，但 *name* 参数除外。

**返回的值**

无。

**异常**

RangeError。

### 51.9.3 成员

TimePoint 对象的成员与 [TimePoint](pt01ch51pyo09.md#ker-timepoint-timepoint-pyc) 方法的参数具有相同的名称和描述。

### 51.9.4 对应的分析关键字

| [*TIME POINTS](../key/key-link.md#usb-kws-htimepoints) |
| --- |
