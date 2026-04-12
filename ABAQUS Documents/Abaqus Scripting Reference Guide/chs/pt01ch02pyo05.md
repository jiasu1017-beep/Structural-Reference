# 2.5 AdaptivityIteration 对象





AdaptivityIteration 对象包含有关变拓扑适应性过程（自适应重网格划分）给定迭代的信息。

**访问**

```
import job
mdb.adaptivityProcesses[*name*].iterations[*i*]
```

### 2.5.1 AdaptivityIteration(...)

此方法创建一个 AdaptivityIteration 对象。

**路径**

```
mdb.adaptivityProcesses[*name*].AdaptivityIteration
```

**必需参数**

*iteration*

一个 Int，指定此迭代在适应性过程中的序列号。

*jobName*

一个 String，指定此迭代运行的作业名称。

*modelName*

一个 String，指定在此迭代中进行分析和重网格划分的模型名称。

*odbPath*

一个 String，指定为此迭代创建的 ODB 文件的路径。

*remeshingErrors*

一个 Int，指定在此迭代的重网格划分期间生成错误的零件实例数量。

**可选参数**

无。

**返回值**

一个 AdaptivityIteration 对象。

**异常**

无。

### 2.5.2 成员

AdaptivityIteration 对象具有与 [AdaptivityIteration](pt01ch02pyo05.md#ker-adaptivityiteration-adaptivityiteration-pyc) 方法参数相同名称和描述的成员。

此外，AdaptivityIteration 对象可以具有以下成员：

*ruleResults*

一个 [RuleResult](pt01ch02pyo12.md) 对象仓库，指定来自此迭代适应性过程的大小函数对应的计算结果。




