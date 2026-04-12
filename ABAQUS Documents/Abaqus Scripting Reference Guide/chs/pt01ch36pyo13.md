# 36.13 OptimizationObjective 对象

OptimizationObjective 是一个用于在目标函数中定义目标的对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].objectiveFunctions[*name*].objectives[*i*]
```

### 36.13.1 成员

OptimizationObjective 对象具有以下成员：

*suppress*

一个布尔值，指定目标是否被抑制。默认值为 OFF。

*weight*

一个 Float，指定应用于设计响应值的权重。默认值为 1.0。

*referenceValue*

SymbolicConstant DEFAULT 或 Float，指定用于评估设计响应的参考值。对于拓扑优化，DEFAULT 表示参考值为 0。对于形状优化，DEFAULT 表示参考值为节点平均值。默认值为 DEFAULT。

*designResponse*

一个字符串，指定设计响应的名称。
