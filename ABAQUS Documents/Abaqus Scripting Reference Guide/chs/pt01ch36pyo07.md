# 36.7 FrozenArea 对象

FrozenArea 对象定义冻结区域几何约束。

FrozenArea 对象派生自 [GeometricRestriction](pt01ch36pyo08.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]
```

### 36.7.1 FrozenArea(...)

此方法创建 FrozenArea 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].FrozenArea
```

**必要参数**

*name*

一个字符串，指定几何约束仓库键。

**可选参数**

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用几何约束的区域。当与 [TopologyTask](pt01ch36pyo41.md) 一起使用时，没有默认值。当与 [ShapeTask](pt01ch36pyo20.md) 一起使用时，默认值为 MODEL。

**返回值**

FrozenArea 对象。

**异常**

无。

### 36.7.2 setValues(...)

此方法修改 FrozenArea 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [FrozenArea](pt01ch36pyo07.md#ker-frozenarea-frozenarea-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.7.3 成员

FrozenArea 对象具有与 [FrozenArea](pt01ch36pyo07.md#ker-frozenarea-frozenarea-pyc) 方法的参数名称和描述相同的成员。
