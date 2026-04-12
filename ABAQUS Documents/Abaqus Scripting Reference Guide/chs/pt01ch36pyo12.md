# 36.12 OptimizationConstraint 对象

OptimizationConstraint 对象约束优化，使其不能改变模型的拓扑。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].optimizationConstraints[*name*]
```

### 36.12.1 OptimizationConstraint(...)

此方法创建 OptimizationConstraint 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].OptimizationConstraint
```

**必要参数**

*name*

一个字符串，指定优化约束仓库键。

*designResponse*

一个字符串，指定要约束的设计响应名称。

*restrictionValue*

一个 Float，指定设计响应应被约束到的值。

**可选参数**

*restrictionMethod*

一个 SymbolicConstant，指定用于约束设计响应的方法。可能的值为 ABSOLUTE_EQUAL、ABSOLUTE_GREATER_THAN_EQUAL、ABSOLUTE_LESS_THAN_EQUAL、RELATIVE_EQUAL、RELATIVE_GREATER_THAN_EQUAL 和 RELATIVE_LESS_THAN_EQUAL。默认值为 ABSOLUTE_EQUAL。

**返回值**

OptimizationConstraint 对象。

**异常**

InvalidNameError 和 RangeError。

### 36.12.2 setValues(...)

此方法修改 OptimizationConstraint 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [OptimizationConstraint](pt01ch36pyo12.md#ker-optimizationconstraint-optimizationconstraint-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 36.12.3 成员

OptimizationConstraint 对象具有与 [OptimizationConstraint](pt01ch36pyo12.md#ker-optimizationconstraint-optimizationconstraint-pyc) 方法的参数名称和描述相同的成员。
