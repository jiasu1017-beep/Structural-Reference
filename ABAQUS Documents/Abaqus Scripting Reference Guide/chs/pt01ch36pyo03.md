# 36.3 DesignDirection 对象

DesignDirection 对象定义设计方向几何约束。

DesignDirection 对象派生自 [GeometricRestriction](pt01ch36pyo08.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]
```

### 36.3.1 DesignDirection(...)

此方法创建 DesignDirection 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].DesignDirection
```

**必要参数**

*name*

一个字符串，指定几何约束仓库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用几何约束的区域。当与 [TopologyTask](pt01ch36pyo41.md) 一起使用时，没有默认值。当与 [ShapeTask](pt01ch36pyo20.md) 一起使用时，默认值为 MODEL。

**可选参数**

*csys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定局部坐标系。如果 *csys*=`None`，则使用全局坐标系。当查询此成员时，它返回一个 Int。默认值为 `None`。

*masterPoint*

`None` 或 [Region](pt01ch45pyo03.md) 对象，指定当 *masterPointDetermination* 为 SPECIFY 时使用的主点。默认值为 `None`。

*masterPointDetermination*

一个 SymbolicConstant，指定分配点优先级的规则。可能的值为 MAXIMUM、MINIMUM 和 SPECIFY。默认值为 MAXIMUM。

*movementRestriction*

一个 SymbolicConstant，指定区域中的移动是否应仅跟随 *masterPoint* 的方向、仅跟随幅值，或同时跟随 *masterPoint* 的幅值和 *u1*、*u2* 及 *u3* 指定的方向。可能的值为 DIRECTION、MAGNITUDE 和 VECTOR。默认值为 VECTOR。

*presumeFeasibleRegionAtStart*

一个布尔值，指定在第一个设计循环中是否忽略几何约束。默认值为 ON。

*u1*

一个布尔值，指定区域中的移动是否应跟随 *masterPoint* 在 1 方向上的移动。当 *movementRestriction* 为 VECTOR 时使用此参数。默认值为 ON。

*u2*

一个布尔值，指定区域中的移动是否应跟随 *masterPoint* 在 2 方向上的移动。当 *movementRestriction* 为 VECTOR 时使用此参数。默认值为 ON。

*u3*

一个布尔值，指定区域中的移动是否应跟随 *masterPoint* 在 3 方向上的移动。当 *movementRestriction* 为 VECTOR 时使用此参数。默认值为 ON。

**返回值**

DesignDirection 对象。

**异常**

无。

### 36.3.2 setValues(...)

此方法修改 DesignDirection 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [DesignDirection](pt01ch36pyo03.md#ker-designdirection-designdirection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.3.3 成员

DesignDirection 对象具有与 [DesignDirection](pt01ch36pyo03.md#ker-designdirection-designdirection-pyc) 方法的参数名称和描述相同的成员。
