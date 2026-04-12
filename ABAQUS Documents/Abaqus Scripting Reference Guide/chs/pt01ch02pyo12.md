# 2.12 RuleResult 对象





RuleResult 对象包含与适应性迭代的 [RemeshingRule](pt01ch02pyo11.md) 对象对应的结果信息。

**访问**

```
import job
mdb.adaptivityProcesses[*name*].iterations[*i*].ruleResults[*name*]
```

### 2.12.1 RuleResult(...)

此方法创建一个 RuleResult，其中包含给定适应性迭代的 [RemeshingRule](pt01ch02pyo11.md) 的数据。

**路径**

```
mdb.adaptivityProcesses[*name*].iterations[*i*].RuleResult
```

**必需参数**

*name*

一个 String，指定这些结果对应的重网格规则名称。

*indicatorResults*

一个 [ErrorIndicatorResult](pt01ch02pyo09.md) 对象仓库，指定重网格规则误差指示器变量对应的大小函数计算结果。

*numElems*

一个 Int，指定重网格划分前该重网格规则区域中的元素数量。

*minSizeElemCount*

一个 Int，指定被重网格规则约束为最小元素尺寸的元素数量。

**可选参数**

*satisfiedVars*

一个 String 序列，指定已满足重网格规则的误差指示器变量。

**返回值**

一个 RuleResult 对象。

**异常**

AbaqusException。

### 2.12.2 成员

RuleResult 对象具有与 [RuleResult](pt01ch02pyo12.md#ker-ruleresult-ruleresult-pyc) 方法参数相同名称和描述的成员。




