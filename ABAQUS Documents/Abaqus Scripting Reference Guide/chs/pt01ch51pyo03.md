# 51.3 FieldOutputRequestState 对象

FieldOutputRequestState 对象存储当前步骤中场输出请求的传播数据。对于每个步骤，[FieldOutputRequest](pt01ch51pyo02.md) 对象会在内部创建一个此对象的实例。该实例也会由 [FieldOutputRequest](pt01ch51pyo02.md) 对象在内部删除。

FieldOutputRequestState 对象没有构造函数或方法。

**访问**

```
import step
mdb.models[*name*].steps[*name*].fieldOutputRequestState[*name*]
```

### 51.3.1 成员

FieldOutputRequestState 对象可以具有以下成员：

*variablesState*

一个 SymbolicConstant，指定场输出请求变量的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*frequency*

SymbolicConstant LAST_INCREMENT 或一个 Int，指定输出频率（以增量计）。默认值为 1。

*frequencyState*

一个 SymbolicConstant，指定场输出请求频率的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*modesState*

一个 SymbolicConstant，指定场输出请求模态的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*timeInterval*

SymbolicConstant EVERY_TIME_INCREMENT 或一个 Float，指定写入输出状态的时间间隔。默认值为 EVERY_TIME_INCREMENT。

*timeIntervalState*

一个 SymbolicConstant，指定场输出请求时间间隔的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*numIntervals*

一个 Int，指定在步骤期间写入输出数据库状态的间隔数。默认值为 20。

*numIntervalsState*

一个 SymbolicConstant，指定场输出请求的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*timeMarks*

一个 Boolean，指定何时将结果写入输出数据库。默认值为 OFF。

*timeMarksState*

一个 SymbolicConstant，指定场输出请求的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*timePointState*

一个 SymbolicConstant，指定场输出请求的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*status*

一个 SymbolicConstant，指定 FieldOutputRequestState 对象的传播状态。可选值为 NOT_YET_ACTIVE、CREATED、PROPAGATED、MODIFIED、DEACTIVATED、NO_LONGER_ACTIVE、TYPE_NOT_APPLICABLE 和 INSTANCE_NOT_APPLICABLE。

*variables*

一个 String 元组，指定输出请求的变量或分量名称，或 SymbolicConstant PRESELECT 或 ALL。PRESELECT 代表给定步骤的所有默认输出变量。ALL 代表所有有效的输出变量。

*modes*

SymbolicConstant ALL 或一个 Int 元组，指定需要输出的特征模态列表。默认值为 ALL。

*timePoint*

一个 String，指定时间点对象的名称，用于确定在时间段内的哪些点将数据写入输出数据库。默认值为空字符串。

*frequencyType*

一个 String，指定一个只读的 SymbolicConstant，描述使用的是哪种类型的输出频率。可选值为 FREQUENCY、NUMBER_INTERVALS、TIME_INTERVAL、TIME_POINT 和 MODES。默认值取决于过程。默认值为空字符串。
