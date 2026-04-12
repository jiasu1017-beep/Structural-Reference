# 51.8 Restart 对象

Restart 对象用于定义重启请求。

**访问**

```
import step
mdb.models[*name*].steps[*name*].restart
```

### 51.8.1 Restart(...)

此方法创建一个重启请求。

**路径**

```
mdb.models[*name*].steps[*name*].Restart
```

**必要参数**

无。

**可选参数**

*numberIntervals*

一个 Int，指定在步骤期间写入重启信息的间隔数。默认值为 0。默认值为 1。

*timeMarks*

一个 Boolean，指定在分析期间写入时是否使用精确时间标记。默认值为 OFF。默认值为 OFF。

*overlay*

一个 Boolean，指定是否仅在重启文件中保留每个步骤的一个增量，从而最小化重启文件的大小。默认值为 OFF。默认值为 ON。

*frequency*

一个 Int，指定写入重启信息的增量间隔。默认值为 0。默认值为 0。

此参数仅适用于 Abaqus/Standard 分析。

**返回的值**

一个 Restart 对象。

**异常**

RangeError。

### 51.8.2 setValues(...)

此方法修改 Restart 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [Restart](pt01ch51pyo08.md#ker-restart-restart-pyc) 方法的参数相同。

**返回的值**

无。

**异常**

RangeError。

### 51.8.3 成员

Restart 对象的成员与 [Restart](pt01ch51pyo08.md#ker-restart-restart-pyc) 方法的参数具有相同的名称和描述。

### 51.8.4 对应的分析关键字

| [*RESTART](../key/key-link.md#usb-kws-mrestart) |
| --- |
