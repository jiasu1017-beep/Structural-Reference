# 36.18 ShapePointSymmetry 对象

ShapePointSymmetry 对象定义形状点对称几何约束。

ShapePointSymmetry 对象派生自 [GeometricRestriction](pt01ch36pyo08.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]
```

### 36.18.1 ShapePointSymmetry(...)

此方法创建 ShapePointSymmetry 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].ShapePointSymmetry
```

**必要参数**

*name*

一个字符串，指定几何约束仓库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用几何约束的区域。当与 [TopologyTask](pt01ch36pyo41.md) 一起使用时，没有默认值。当与 [ShapeTask](pt01ch36pyo20.md) 一起使用时，默认值为 MODEL。

**可选参数**

*csys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，将对称点指定为局部坐标系的原点。如果 *csys*=`None`，则使用全局坐标系。当查询此成员时，它返回一个 Int。默认值为 `None`。

*masterPointDetermination*

一个 SymbolicConstant，指定确定主节点的规则。可能的值为 MAXIMUM 和 MINIMUM。默认值为 MAXIMUM。

*presumeFeasibleRegionAtStart*

一个布尔值，指定在第一个设计循环中是否忽略几何约束。默认值为 ON。

*tolerance1*

一个 Float，指定 1 方向的几何公差。默认值为 0.01。

*tolerance2*

一个 Float，指定 2 方向的几何公差。默认值为 0.01。

*tolerance3*

一个 Float，指定 3 方向的几何公差。默认值为 0.01。

**返回值**

ShapePointSymmetry 对象。

**异常**

无。

### 36.18.2 setValues(...)

此方法修改 ShapePointSymmetry 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [ShapePointSymmetry](pt01ch36pyo18.md#ker-shapepointsymmetry-shapepointsymmetry-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.18.3 成员

ShapePointSymmetry 对象具有与 [ShapePointSymmetry](pt01ch36pyo18.md#ker-shapepointsymmetry-shapepointsymmetry-pyc) 方法的参数名称和描述相同的成员。
