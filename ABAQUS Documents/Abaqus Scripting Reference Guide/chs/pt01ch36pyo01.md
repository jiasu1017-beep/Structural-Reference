# 36.1 OptimizationTask 对象

OptimizationTask 对象是其他 OptimizationTask 对象的抽象基类型。OptimizationTask 对象没有显式构造函数。OptimizationTask 对象的方法和成员对从 OptimizationTask 派生的所有对象都是通用的。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*]
```

### 36.1.1 成员

OptimizationTask 对象可以具有以下成员：

*name*

一个字符串，指定优化任务仓库键。

*region*

SymbolicConstant MODEL 或 [Region](pt01ch45pyo03.md) 对象，指定应用优化任务的区域。默认值为 MODEL。

*designResponses*

[DesignResponse](pt01ch36pyo04.md) 对象的仓库。

*objectiveFunctions*

[ObjectiveFunction](pt01ch36pyo11.md) 对象的仓库。

*optimizationConstraints*

[OptimizationConstraint](pt01ch36pyo12.md) 对象的仓库。

*geometricRestrictions*

[GeometricRestriction](pt01ch36pyo08.md) 对象的仓库。

*stopConditions*

[StopCondition](pt01ch36pyo34.md) 对象的仓库。
