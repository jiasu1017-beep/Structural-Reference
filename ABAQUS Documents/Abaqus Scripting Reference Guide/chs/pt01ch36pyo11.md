# 36.11 ObjectiveFunction 对象

ObjectiveFunction 对象定义优化的目标。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].objectiveFunctions[*name*]
```

### 36.11.1 ObjectiveFunction(...)

此方法创建 ObjectiveFunction 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].ObjectiveFunction
```

**必要参数**

*name*

一个字符串，指定目标函数仓库键。

*objectives*

一个 [OptimizationObjectiveArray](pt01ch36pyo13.md) 对象。

**可选参数**

*target*

一个 SymbolicConstant，指定目标函数的目标。可能的值为 MINIMIZE、MAXIMIZE 和 MINIMIZE_MAXIMUM。默认值为 MINIMIZE。

**返回值**

ObjectiveFunction 对象。

**异常**

InvalidNameError 和 RangeError。

### 36.11.2 setValues(...)

此方法修改 ObjectiveFunction 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [ObjectiveFunction](pt01ch36pyo11.md#ker-objectivefunction-objectivefunction-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 36.11.3 成员

ObjectiveFunction 对象具有与 [ObjectiveFunction](pt01ch36pyo11.md#ker-objectivefunction-objectivefunction-pyc) 方法的参数名称和描述相同的成员。
