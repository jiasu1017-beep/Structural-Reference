# 34.11 JobData 对象

JobData 对象描述运行分析的环境。

**访问**

```
import odbAccess
session.odbs[*name*].jobData
```

### 34.11.1 成员

JobData 对象具有以下成员：

*name*

一个字符串，指定作业名称。

*analysisCode*

一个 SymbolicConstant，指定分析代码。可能的值为 ABAQUS_STANDARD、ABAQUS_EXPLICIT 和 UNKNOWN_ANALYSIS_CODE。

*precision*

一个 SymbolicConstant，指定精度。当前仅支持 SINGLE_PRECISION。可能的值为 DOUBLE_PRECISION 和 SINGLE_PRECISION。

*version*

一个字符串，指定分析代码的版本。

*creationTime*

一个字符串，指定运行分析的日期和时间。

*modificationTime*

一个字符串，指定数据库上次修改的日期和时间。

*machineName*

一个字符串，指定运行分析的机器名称。

*productAddOns*

一个字符串，指定 odb_Sequence 的 productAddOns。可能的值为：AQUA、DESIGN、BIORID、CEL、SOLITER 和 CAVPARALLEL。
