# 32.1 DataObject 对象

DataObject 对象的实例被传递给每个回调。DataObject 对象没有方法。DataObject 对象的成员取决于对象的类型。所有 DataObject 实例都具有以下成员，无论类型如何：
- *clientHost*
- *clientName*
- *phase*
- *processId*
- *threadId*
- *timeStamp*

可能的 DataObject 类型及各类型的附加成员如下：

** ABORTED **

- *message*

** COMPLETED **

- *message*

** END_STEP **

- *stepId*

** ERROR **

- *message*

** HEADING **

- *heading*

** MONITOR_DATA **

- *dof*
- *node*
- *nset*
- *procedure*
- *time*
- *value*

** ODB_FILE **

- *file*

** STARTED **

- 无附加成员。

** STATUS **

- *attempts*
- *equilibrium*
- *increment*
- *iterations*
- *severe*
- *step*
- *stepTime*
- *timeIncrement*
- *totalTime*

** STEP **

- *stepId*
- *stepName*

** WARNING **

- *message*

### 32.1.1 成员

DataObject 对象具有以下成员：

*phase*

一个 SymbolicConstant，指定分析阶段。可能的值为 BATCHPRE_PHASE、PACKAGER_PHASE、STANDARD_PHASE、EXPLICIT_PHASE、CALCULATOR_PHASE 和 UNKNOWN_PHASE。

*processId*

一个整数，指定分析产品的进程 ID。

*threadId*

一个整数，指定分析产品的线程 ID。线程用于并行或多处理；在大多数情况下 *threadId* 设置为零。

*timeStamp*

一个整数，指定消息发送的时间（自 1970 年 1 月 1 日 00:00:00 UTC 以来的秒数）。

*attempts*

一个整数，指定在此步骤中达到平衡的尝试次数。

*dof*

一个整数，指定请求监测输出的自由度。

*equilibrium*

一个整数，指定在此增量期间进行的平衡迭代次数。

*increment*

一个整数，指定分析的增量。

*iterations*

一个整数，指定步骤中的迭代次数。

*node*

一个整数，指定请求监测输出的节点号。

*severe*

一个整数，指定在此增量期间完成的严重不连续迭代次数。

*step*

一个整数，指定当前步骤号。步骤号 1 对应第一个步骤。

*stepId*

一个整数，指定步骤的 ID。

*stepTime*

一个 Float，指定当前增量对应的步骤时间。

*time*

一个 Float，指定与监测数据对应的总时间。

*timeIncrement*

一个 Float，指定当前步骤中使用的時間增量。

*totalTime*

一个 Float，指定分析中完成的总时间。

*value*

一个 Float，指定请求监测的自由度的当前值。

*clientHost*

一个字符串，指定运行分析的机器的主机名。

*clientName*

一个字符串，指定响应回调函数的客户端名称。可能的值为"BatchPre"、"Packager"、"Standard"、"Explicit"和"Calculator"。

*file*

一个字符串，指定输出数据库的完整路径。

*heading*

一个字符串，指定作业标题。

*message*

一个字符串，指定作业标题。

*nset*

一个字符串，指定为监测输出指定的节点集。

*stepName*

一个字符串，指定步骤的名称。
