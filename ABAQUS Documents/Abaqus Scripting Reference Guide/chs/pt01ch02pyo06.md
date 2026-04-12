# 2.6 AdaptivityProcess 对象





AdaptivityProcess 对象定义将提交进行分析的一系列作业。Abaqus 在每个作业之间执行自适应重网格划分。

**访问**

```
import job
mdb.adaptivityProcesses[*name*]
```

### 2.6.1 AdaptivityProcess(...)

此方法创建一个 AdaptivityProcess 对象。

**路径**

```
mdb.AdaptivityProcess
```

**必需参数**

*name*

一个 String，指定适应性过程的名称。

*job*

一个 [ModelJob](pt01ch26pyo04.md) 对象，指定用作适应性过程运行的所有分析作业原型的作业。

**可选参数**

*maxIterations*

一个 Int，指定适应性过程将运行的最大分析作业数。Abaqus 在每次分析之间执行自适应重网格划分。默认值为 3。

*jobPrefix*

一个 String，指定适应性过程创建的作业的前缀。空字符串表示应使用适应性过程的名称。默认值为空字符串。

**返回值**

一个 AdaptivityProcess 对象。

**异常**

AbaqusException。

### 2.6.2 submit(...)

此方法开始分析和自适应重网格划分过程。

**必需参数**

无。

**可选参数**

*waitForCompletion*

一个 Boolean，指定是否中断脚本的执行直到自适应重网格划分过程结束。

*datacheckJob*

一个 Boolean，指定是否将适应性作为 datacheck 分析运行。默认值为 False。datacheckJob 和 continueJob 参数不能同时为 True。

*continueJob*

一个 Boolean，指定是否将适应性作为继续分析运行。默认值为 False。datacheckJob 和 continueJob 参数不能同时为 True。

**返回值**

无

**异常**

无。

### 2.6.3 setValues(...)

此方法修改 AdaptivityProcess 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [AdaptivityProcess](pt01ch02pyo06.md#ker-adaptivityprocess-adaptivityprocess-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

### 2.6.4 成员

AdaptivityProcess 对象具有与 [AdaptivityProcess](pt01ch02pyo06.md#ker-adaptivityprocess-adaptivityprocess-pyc) 方法参数相同名称和描述的成员。

此外，AdaptivityProcess 对象可以具有以下成员：

*status*

一个 SymbolicConstant，指定适应性过程的状态。可能的值为 SUBMITTED、RUNNING、ABORTED、TERMINATED 和 COMPLETED。

*iterations*

一个 [AdaptivityIteration](pt01ch02pyo05.md) 对象仓库，指定在运行适应性过程期间接收到的 [AdaptivityIteration](pt01ch02pyo05.md) 对象。




