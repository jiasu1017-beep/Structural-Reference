# 2.1 AdaptiveMeshConstraint 对象





AdaptiveMeshConstraint 对象是其他任意拉格朗日欧拉（ALE）样式 AdaptiveMeshConstraint 对象的抽象基类型。AdaptiveMeshConstraint 对象没有显式构造函数。AdaptiveMeshConstraint 对象的方法和成员对从 AdaptiveMeshConstraint 对象派生的所有对象都是通用的。

**访问**

```
import step
mdb.models[*name*].adaptiveMeshConstraints[*name*]
```

### 2.1.1 deactivate(...)

此方法在指定步骤及所有后续步骤中停用自适应网格约束。

**必需参数**

*stepName*

一个 String，指定要停用自适应网格约束的步骤名称。

**可选参数**

无。

**返回值**

无

**异常**

TextError。

### 2.1.2 move(...)

此方法将自适应网格约束状态从一个步骤移动到不同的步骤。

**必需参数**

*fromStepName*

一个 String，指定要移动其自适应网格约束状态的步骤名称。

*toStepName*

一个 String，指定要将自适应网格约束状态移动到的步骤名称。

**可选参数**

无。

**返回值**

无

**异常**

TextError。

### 2.1.3 reset(...)

此方法将指定步骤的自适应网格约束状态重置为前一个分析步骤的状态。

**必需参数**

*stepName*

一个 String，指定要重置自适应网格约束状态的步骤名称。

**可选参数**

无。

**返回值**

无

**异常**

TextError。

### 2.1.4 resume()

此方法恢复之前抑制的自适应网格约束。

**参数**

无。

**返回值**

无

**异常**

无。

### 2.1.5 suppress()

此方法抑制自适应网格约束。

**参数**

无。

**返回值**

无

**异常**

无。

### 2.1.6 delete(...)

此方法允许您删除现有的自适应网格约束。

**必需参数**

*indices*

一个 Int 序列，指定要删除的每个自适应网格约束的索引。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 2.1.7 成员

AdaptiveMeshConstraint 对象可以具有以下成员：

*name*

一个 String，指定自适应网格约束仓库键。

*category*

一个 SymbolicConstant，指定自适应网格约束的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用自适应网格约束的区域。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定自适应网格约束自由度的局部坐标系。如果 *localCsys*=`None`，则在全局坐标系中定义自由度。默认值为 `None`。




