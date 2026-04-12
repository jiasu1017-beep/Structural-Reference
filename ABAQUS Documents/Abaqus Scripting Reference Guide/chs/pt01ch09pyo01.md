# 9.1 BoundaryCondition 对象

BoundaryCondition 对象是其他 BoundaryCondition 对象的抽象基类型。BoundaryCondition 对象没有显式构造函数。BoundaryCondition 对象的方法和成员对所有派生自 BoundaryCondition 的对象都是通用的。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.1.1 deactivate(...)

此方法在指定步骤及所有后续步骤中停用边界条件。

**必需参数**

*stepName*

一个 String，指定要停用边界条件的步骤名称。

**可选参数**

无。

**返回值**

无。

**异常**

TextError。

### 9.1.2 move(...)

此方法将边界条件状态从一个步骤移动到不同的步骤。

**必需参数**

*fromStepName*

一个 String，指定要移出边界条件状态的步骤名称。

*toStepName*

一个 String，指定要移入边界条件状态的步骤名称。

**可选参数**

无。

**返回值**

无。

**异常**

TextError。

### 9.1.3 reset(...)

此方法将指定步骤的边界条件状态重置为前一个分析步骤的状态。

**必需参数**

*stepName*

一个 String，指定要重置边界条件状态的步骤名称。

**可选参数**

无。

**返回值**

无。

**异常**

TextError。

### 9.1.4 resume()

此方法恢复先前被抑制的边界条件。

**参数**

无。

**返回值**

无。

**异常**

无。

### 9.1.5 suppress()

此方法抑制边界条件。

**参数**

无。

**返回值**

无。

**异常**

无。

### 9.1.6 delete(...)

此方法允许删除现有边界条件。

**必需参数**

*indices*

一个 Int 序列，指定要删除的每个边界条件的索引。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 9.1.7 成员

BoundaryCondition 对象可以具有以下成员：

*name*

一个 String，指定边界条件存储库键。

*category*

一个 SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用边界条件的区域。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
