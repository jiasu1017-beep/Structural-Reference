# 36.10 LocalStopCondition 对象

LocalStopCondition 对象定义局部停止条件。

LocalStopCondition 对象派生自 [StopCondition](pt01ch36pyo34.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].stopConditions[*name*]
```

### 36.10.1 LocalStopCondition(...)

此方法创建 LocalStopCondition 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].LocalStopCondition
```

**必要参数**

*name*

一个字符串，指定停止条件仓库键。

*referenceFactor*

一个 Float，指定用于修改参考值的因子。

**可选参数**

*comparisonOperation*

一个 SymbolicConstant，指定用于将所选值与参考值进行比较的操作。可能的值为 LESS_THAN、LESS_THAN_EQUAL、EQUAL、GREATER_THAN_EQUAL 和 GREATER_THAN。默认值为 LESS_THAN。

*identifier*

一个 SymbolicConstant，指定比较值的变量标识符。可能的值为：
- ABSOLUTE_GROWTH_MOVEMENT
- ABSOLUTE_SHRINK_MOVEMENT
- GROWTH_MOVEMENT
- SHRINK_MOVEMENT
- MOVEMENT
- TOTAL_ABSOLUTE_MOVEMENT
- EQUIV_STRESS
- FREE_TASK_REGION_EQUIV_STRESS
- RESTRICTED_TASK_REGION_EQUIV_STRESS
- SURFACE_POINT_EQUIV_STRESS
- TASK_REGION_EQUIV_STRESS

默认值为 MOVEMENT。

*identifierOperation*

一个 SymbolicConstant，指定用于评估区域中值的操作。可能的值为 MAXIMUM、MINIMUM 和 SUM。默认值为 MAXIMUM。

*referenceDesignCycle*

一个 SymbolicConstant，指定从哪个迭代中比较值与参考值。可能的值为 FIRST 和 PREVIOUS。默认值为 PREVIOUS。

*referenceOperation*

一个 SymbolicConstant，指定用于通过参考因子修改参考值的操作。可能的值为 ADD、DIVIDE、MULTIPLY 和 SUBTRACT。默认值为 ADD。

*region*

SymbolicConstant MODEL 或 [Region](pt01ch45pyo03.md) 对象，指定应用停止条件的区域。默认值为 MODEL。

**返回值**

LocalStopCondition 对象。

**异常**

无。

### 36.10.2 setValues(...)

此方法修改 LocalStopCondition 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [LocalStopCondition](pt01ch36pyo10.md#ker-localstopcondition-localstopcondition-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.10.3 成员

LocalStopCondition 对象具有与 [LocalStopCondition](pt01ch36pyo10.md#ker-localstopcondition-localstopcondition-pyc) 方法的参数名称和描述相同的成员。
