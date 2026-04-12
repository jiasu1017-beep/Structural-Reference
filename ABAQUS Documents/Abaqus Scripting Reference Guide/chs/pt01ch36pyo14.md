# 36.14 PenetrationCheck 对象

PenetrationCheck 对象定义穿透检查几何约束。

PenetrationCheck 对象派生自 [GeometricRestriction](pt01ch36pyo08.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]
```

### 36.14.1 PenetrationCheck(...)

此方法创建 PenetrationCheck 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].PenetrationCheck
```

**必要参数**

*name*

一个字符串，指定几何约束仓库键。

*penetrationCheckRegion*

一个 [Region](pt01ch45pyo03.md) 对象，指定穿透检查区域。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用几何约束的区域。当与 [TopologyTask](pt01ch36pyo41.md) 一起使用时，没有默认值。当与 [ShapeTask](pt01ch36pyo20.md) 一起使用时，默认值为 MODEL。

**可选参数**

*presumeFeasibleRegionAtStart*

一个布尔值，指定在第一个设计循环中是否忽略几何约束。默认值为 ON。

**返回值**

PenetrationCheck 对象。

**异常**

无。

### 36.14.2 setValues(...)

此方法修改 PenetrationCheck 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [PenetrationCheck](pt01ch36pyo14.md#ker-penetrationcheck-penetrationcheck-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.14.3 成员

PenetrationCheck 对象具有与 [PenetrationCheck](pt01ch36pyo14.md#ker-penetrationcheck-penetrationcheck-pyc) 方法的参数名称和描述相同的成员。
