# 36.16 ShapeMemberSize 对象

ShapeMemberSize 对象定义形状成员尺寸几何约束。

ShapeMemberSize 对象派生自 [GeometricRestriction](pt01ch36pyo08.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]
```

### 36.16.1 ShapeMemberSize(...)

此方法创建 ShapeMemberSize 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].ShapeMemberSize
```

**必要参数**

*name*

一个字符串，指定几何约束仓库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用几何约束的区域。当与 [TopologyTask](pt01ch36pyo41.md) 一起使用时，没有默认值。当与 [ShapeTask](pt01ch36pyo20.md) 一起使用时，默认值为 MODEL。

**可选参数**

*maxThickness*

一个 Float，指定最大厚度。默认值为 0.0。

*minThickness*

一个 Float，指定最小厚度。默认值为 0.0。

*sizeRestriction*

一个 SymbolicConstant，指定是限制最小厚度还是最大厚度。可能的值为 MAXIMUM 和 MINIMUM。默认值为 MINIMUM。

**返回值**

ShapeMemberSize 对象。

**异常**

无。

### 36.16.2 setValues(...)

此方法修改 ShapeMemberSize 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [ShapeMemberSize](pt01ch36pyo16.md#ker-shapemembersize-shapemembersize-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.16.3 成员

ShapeMemberSize 对象具有与 [ShapeMemberSize](pt01ch36pyo16.md#ker-shapemembersize-shapemembersize-pyc) 方法的参数名称和描述相同的成员。
