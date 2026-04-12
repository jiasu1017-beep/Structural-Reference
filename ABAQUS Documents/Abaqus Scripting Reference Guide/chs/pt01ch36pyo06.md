# 36.6 FixedRegion 对象

FixedRegion 对象定义固定区域几何约束。

FixedRegion 对象派生自 [GeometricRestriction](pt01ch36pyo08.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]
```

### 36.6.1 FixedRegion(...)

此方法创建 FixedRegion 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].FixedRegion
```

**必要参数**

*name*

一个字符串，指定几何约束仓库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用几何约束的区域。当与 [TopologyTask](pt01ch36pyo41.md) 一起使用时，没有默认值。当与 [ShapeTask](pt01ch36pyo20.md) 一起使用时，默认值为 MODEL。

**可选参数**

*csys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定局部坐标系。如果 *csys*=`None`，则使用全局坐标系。当查询此成员时，它返回一个 Int。默认值为 `None`。

*presumeFeasibleRegionAtStart*

一个布尔值，指定在第一个设计循环中是否忽略几何约束。默认值为 ON。

*u1*

一个布尔值，指定是否在 1 方向上固定区域。默认值为 OFF。

*u2*

一个布尔值，指定是否在 2 方向上固定区域。默认值为 OFF。

*u3*

一个布尔值，指定是否在 3 方向上固定区域。默认值为 OFF。

**返回值**

FixedRegion 对象。

**异常**

无。

### 36.6.2 setValues(...)

此方法修改 FixedRegion 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [FixedRegion](pt01ch36pyo06.md#ker-fixedregion-fixedregion-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.6.3 成员

FixedRegion 对象具有与 [FixedRegion](pt01ch36pyo06.md#ker-fixedregion-fixedregion-pyc) 方法的参数名称和描述相同的成员。
