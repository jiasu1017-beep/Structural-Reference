# 26.3 Message 对象

Message 对象包含有关模拟特定阶段的信息。如果脚本在没有 Abaqus/CAE GUI（使用 `noGUI` 选项）的情况下运行，则不会返回作业消息。

**访问**

```
import job
mdb.coexecutions[*name*].jobs[*name*].messages[*i*]
mdb.jobs[*name*].messages[*i*]
```

### 26.3.1 成员

Message 对象具有以下成员：

*type*

 SymbolicConstant，指定消息类型。可能的值为：
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
- STARTED
- STATE_FRAME
- STATUS
- STEP
- WARNING

*data*

[Dictionary](#ker-dictionary-pyc) 对象，指定分析产品返回的数据。值取决于返回的消息有关 [DataObject](pt01ch32pyo01.md) 的成员列表。





