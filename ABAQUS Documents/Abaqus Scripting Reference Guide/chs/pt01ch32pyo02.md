# 32.2 MonitorMgr 对象

导入 abaqus 模块时会创建 MonitorMgr 对象的一个实例。不需要其他 MonitorMgr 实例。（此 MonitorMgr 对象不要与从 [Step](pt01ch49pyo01.md) 对象构建的自由度（DOF）监视器混淆。）

**访问**

```
monitorManager
```

### 32.2.1 addMessageCallback(...)

此方法指定一个回调函数，当从分析产品收到指定消息时将调用该函数。

有关更多信息，请参阅《Abaqus Scripting User's Guide》第 6.8.3 节"回调函数示例"。

**必要参数**

*jobName*

一个字符串，指定要监视的作业名称或 SymbolicConstant ANY_JOB。

*messageType*

一个 SymbolicConstant，指定哪种消息类型将调用此回调。可能的值为：
- ABORTED
- ANY_JOB
- ANY_MESSAGE_TYPE
- COMPLETED
- END_STEP
- ERROR
- HEADING
- HEALER_JOB
- HEALER_TYPE
- INTERRUPTED
- ITERATION
- JOB_ABORTED
- JOB_COMPLETED
- JOB_INTERRUPTED
- JOB_SUBMITTED
- MONITOR_DATA
- ODB_FILE
- ODB_FRAME
- SIMULATION_ABORTED
- SIMULATION_COMPLETED
- SIMULATION_INTERRUPTED
- SIMULATION_SUBMITTED
- STARTED
- STATUS
- STEP
- WARNING

*callback*

要调用的 Python 函数。回调函数的接口定义如下：

```
def onMessage(*jobName*, *messageType*, *data*, *userData*)
```

- *jobName* 是一个字符串。
- *messageType* 是一个 SymbolicConstant，可能的值与之前为 `addMessageCallback` 方法列出的相同。
- *data* 是一个 [DataObject](pt01ch32pyo01.md) 对象。
- *userData* 是作为 *userData* 参数传递给 `addMessageCallback` 方法的对象。

**可选参数**

*userData*

任何 Python 对象或 `None`。此对象被传递给回调函数。

**返回值**

无

**异常**

无。

### 32.2.2 removeMessageCallback(...)

此方法移除一个回调函数。使用添加回调时使用的相同参数来指定要移除的回调函数。

**必要参数**

*jobName*

一个字符串，指定要监视的作业名称或 SymbolicConstant ANY_JOB。

*messageType*

一个 SymbolicConstant，指定哪种消息类型将调用此回调。可能的值为：
- ABORTED
- ANY_JOB
- ANY_MESSAGE_TYPE
- COMPLETED
- END_STEP
- ERROR
- HEADING
- HEALER_JOB
- HEALER_TYPE
- INTERRUPTED
- ITERATION
- JOB_ABORTED
- JOB_COMPLETED
- JOB_INTERRUPTED
- JOB_SUBMITTED
- MONITOR_DATA
- ODB_FILE
- ODB_FRAME
- SIMULATION_ABORTED
- SIMULATION_COMPLETED
- SIMULATION_INTERRUPTED
- SIMULATION_SUBMITTED
- STARTED
- STATUS
- STEP
- WARNING

*callback*

要调用的 Python 函数；它必须与原始调用 `addMessageCallback` 时指定的 *callback* 参数相同。

*userData*

任何 Python 对象或 `None`；它必须与原始调用 `addMessageCallback` 时指定的 *userData* 参数相同。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 32.2.3 checkMonitorStatus()

如果监视状态不是 ENABLED，此方法会引发 MonitorError 异常。

**参数**

无。

**返回值**

无

**异常**

MonitorError：

```
Status is not ENABLED
```

### 32.2.4 成员

MonitorMgr 对象没有成员。
