# 36.9 Growth 对象

Growth 对象定义生长几何约束。

Growth 对象派生自 [GeometricRestriction](pt01ch36pyo08.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]
```

### 36.9.1 Growth(...)

此方法创建 Growth 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].Growth
```

**必要参数**

*name*

一个字符串，指定几何约束仓库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用几何约束的区域。当与 [TopologyTask](pt01ch36pyo41.md) 一起使用时，没有默认值。当与 [ShapeTask](pt01ch36pyo20.md) 一起使用时，默认值为 MODEL。

**可选参数**

*growth*

一个 Float，指定生长方向的最大优化位移。必须指定 *growth* 或 *shrink* 或两者都指定。默认值为 0.0。

*presumeFeasibleRegionAtStart*

一个布尔值，指定在第一个设计循环中是否忽略几何约束。默认值为 ON。

*shrink*

一个 Float，指定收缩方向的最大优化位移。必须指定 *growth* 或 *shrink* 或两者都指定。默认值为 0.0。

**返回值**

Growth 对象。

**异常**

无。

### 36.9.2 setValues(...)

此方法修改 Growth 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [Growth](pt01ch36pyo09.md#ker-growth-growth-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.9.3 成员

Growth 对象具有与 [Growth](pt01ch36pyo09.md#ker-growth-growth-pyc) 方法的参数名称和描述相同的成员。
