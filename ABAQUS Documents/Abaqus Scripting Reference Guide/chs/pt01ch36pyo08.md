# 36.8 GeometricRestriction 对象

GeometricRestriction 对象是其他 GeometricRestriction 对象的抽象基类型。GeometricRestriction 对象没有显式构造函数。GeometricRestriction 对象的方法和成员对所有从 GeometricRestriction 派生的对象都是通用的。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]
```

### 36.8.1 成员

GeometricRestriction 对象可以具有以下成员：

*name*

一个字符串，指定几何约束仓库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用几何约束的区域。当与 [TopologyTask](pt01ch36pyo41.md) 一起使用时，没有默认值。当与 [ShapeTask](pt01ch36pyo20.md) 一起使用时，默认值为 MODEL。
