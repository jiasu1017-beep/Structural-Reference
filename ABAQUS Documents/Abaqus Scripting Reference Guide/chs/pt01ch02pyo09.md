# 2.9 ErrorIndicatorResult 对象





ErrorIndicatorResult 对象包含与适应性迭代的 [RemeshingRule](pt01ch02pyo11.md) 对象中的误差指示器变量对应的结果信息。

**访问**

```
import job
mdb.adaptivityProcesses[*name*].iterations[*i*].ruleResults[*name*]\
.indicatorResults[*name*]
```

### 2.9.1 ErrorIndicatorResult(...)

此方法创建一个 ErrorIndicatorResult，其中包含给定适应性迭代的 [RemeshingRule](pt01ch02pyo11.md) 中误差指示器变量的数据。

**路径**

```
mdb.adaptivityProcesses[*name*].iterations[*i*].ruleResults[*name*]\
.ErrorIndicatorResult
```

**必需参数**

*name*

一个 String，指定这些结果对应的误差指示器变量名称。

*results*

一个 String-to-Float Dictionary，指定由该 ErrorIndicatorResult 表示的误差指示器变量的大小函数计算结果。

**可选参数**

无。

**返回值**

一个 ErrorIndicatorResult 对象。

**异常**

AbaqusException。

### 2.9.2 成员

ErrorIndicatorResult 对象具有与 [ErrorIndicatorResult](pt01ch02pyo09.md#ker-errorindicatorresult-errorindicatorresult-pyc) 方法参数相同名称和描述的成员。




