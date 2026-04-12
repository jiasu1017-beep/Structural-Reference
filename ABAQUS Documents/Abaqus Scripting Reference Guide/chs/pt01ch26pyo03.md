# 26.2 JobFromInputFile 对象

JobFromInputFile 对象定义分析包含在输入文件中的模型的 [Job](pt01ch26pyo01.md) 对象。

JobFromInputFile 对象派生自 [Job](pt01ch26pyo01.md) 对象。

**访问**

```
import job
mdb.jobs[*name*]
```

### 26.2.1 JobFromInputFile(...)

此方法使用输入文件创建分析作业以获取模型定义。

**路径**

```
mdb.JobFromInputFile
```

**必需参数**

*name*

字符串，指定新作业的名称。名称必须是有效的 Abaqus/CAE 对象名称。

*inputFileName*

字符串，指定要读取的输入文件。可能的值为任何有效的文件名。如果参数值中未包含 `.inp` 扩展名，系统将为您追加。

**可选参数**

*type*

 SymbolicConstant，指定作业类型。可能的值为 ANALYSIS、SYNTAXCHECK、RECOVER 和 RESTART。默认值为 ANALYSIS。

如果对象具有类型 JobFromInputFile，则 *type*=RESTART 不可用。

*queue*

字符串，指定要向其提交作业的队列名称。默认值为空字符串。

**注：**在 Windows 工作站上创建 Job 对象时可以使用 *queue* 参数；但远程队列仅在 UNIX 平台上可用。

*waitHours*

整数，指定提交作业前等待的小时数。如果设置了 *queue*，则此参数被忽略。默认值为 0。

此参数与 *waitMinutes* 配合使用。*waitHours* 和 *atTime* 互斥。

*waitMinutes*

整数，指定提交作业前等待的分钟数。如果设置了 *queue*，则此参数被忽略。默认值为 0。

此参数与 *waitHours* 配合使用。*waitMinutes* 和 *atTime* 互斥。

*atTime*

字符串，指定提交作业的时间。如果 *queue* 为空，字符串语法必须对 UNIX `at` 命令有效。如果设置了 *queue*，则语法必须根据系统管理员的要求有效。默认值为空字符串。

**注：**在 Windows 工作站上创建 Job 对象时可以使用 *atTime* 参数；但 `at` 命令仅在 UNIX 平台上可用。

*scratch*

字符串，指定临时目录的位置。默认值为空字符串。

*userSubroutine*

字符串，指定包含用户子程序定义的文件。默认值为空字符串。

*numCpus*

整数，指定用于此分析的 CPU 数量（如果可用并行处理）。可能的值为 *numCpus* ![](../graphics/ker_eqn00060.gif) 0。默认值为 1。

*memory*

整数，指定 Abaqus 分析可用的内存量。值应以 *memoryUnits* 提供的单位表示。默认值为 90。

*memoryUnits*

 SymbolicConstant，指定 Abaqus 分析中使用的内存单位。可能的值为 PERCENTAGE、MEGA_BYTES 和 GIGA_BYTES。默认值为 PERCENTAGE。

*explicitPrecision*

 SymbolicConstant，指定是否使用 Abaqus/Explicit 的双精度版本。可能的值为 SINGLE、FORCE_SINGLE、DOUBLE、DOUBLE_CONSTRAINT_ONLY 和 DOUBLE_PLUS_PACK。默认值为 SINGLE。

*nodalOutputPrecision*

 SymbolicConstant，指定写入输出数据库的节点输出的精度。可能的值为 SINGLE 和 FULL。默认值为 SINGLE。

*parallelizationMethodExplicit*

 SymbolicConstant，指定 Abaqus/Explicit 的并行化方法。可能的值为 LOOP 和 DOMAIN。默认值为 LOOP。

*numDomains*

整数，指定在 Abaqus/Explicit 中并行执行的域数。当 *parallelizationMethodExplicit*=DOMAIN 时，*numDomains* 必须是 *numCpus* 的倍数。默认值为 1。

*activateLoadBalancing*

布尔值，指定是否为 Abaqus/Explicit 中在多个处理器和多个域上运行的作业激活动态负载平衡。默认值为 OFF。

*multiprocessingMode*

 SymbolicConstant，指定分析是分解为线程还是分解为通过消息传递接口 (MPI) 通信的多个进程。可能的值为 DEFAULT、THREADS 和 MPI。默认值为 DEFAULT。

**返回值**

JobFromInputFile 对象。

**异常**

AbaqusException。

### 26.2.2 setValues(...)

此方法修改 JobFromInputFile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [JobFromInputFile](pt01ch26pyo02.md#ker-jobfrominputfile-jobfrominputfile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

### 26.2.3 成员

JobFromInputFile 对象的成员与 [JobFromInputFile](pt01ch26pyo02.md#ker-jobfrominputfile-jobfrominputfile-pyc) 方法的参数具有相同的名称和描述。

此外，JobFromInputFile 对象可以具有以下成员：

*getMemoryFromAnalysis*

布尔值，指定是否从上次数据检查或分析运行中检索建议的内存设置，并在后续提交中使用这些值。默认值为 ON。

*analysis*

 SymbolicConstant，指定作业将由 Abaqus/Standard、Abaqus/Explicit 还是 Abaqus/CFD 分析。可能的值为 STANDARD、EXPLICIT、CFD 和 UNKNOWN。

如果对象具有类型 JobFromInputFile，则 *analysis*=UNKNOWN。

*status*

 SymbolicConstant，指定分析的状态。可能的值为 SUBMITTED、RUNNING、ABORTED、TERMINATED、COMPLETED、CHECK_RUNNING 和 CHECK_COMPLETED。

如果 *message* 成员为空，则 *status* 设置为 NONE。

*messages*

[MessageArray](pt01ch26pyo03.md) 对象，指定分析期间收到的消息。

*environment*

字符串元组，指定环境变量及其值。





