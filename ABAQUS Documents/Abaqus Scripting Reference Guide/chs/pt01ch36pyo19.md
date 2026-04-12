# 36.19 ShapeRotationalSymmetry 对象

ShapeRotationalSymmetry 对象定义形状旋转对称几何约束。

ShapeRotationalSymmetry 对象派生自 [GeometricRestriction](pt01ch36pyo08.md) 对象。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].geometricRestrictions[*name*]
```

### 36.19.1 ShapeRotationalSymmetry(...)

此方法创建 ShapeRotationalSymmetry 对象。

**路径**

```
mdb.models[*name*].optimizationTasks[*name*].ShapeRotationalSymmetry
```

**必要参数**

*name*

一个字符串，指定几何约束仓库键。

*clientDirection*

一个 [VertexArray](pt01ch07pyo15.md) 对象，长度为 2，指定位于 *csys* 原点处的向量，用作对称轴。每个点可以通过坐标元组指定，而不是通过 [Vertex](pt01ch07pyo15.md)。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用几何约束的区域。当与 [TopologyTask](pt01ch36pyo41.md) 一起使用时，没有默认值。当与 [ShapeTask](pt01ch36pyo20.md) 一起使用时，默认值为 MODEL。

**可选参数**

*angle*

一个 Float，指定重复图案的段大小（度）。如果 *angle* 值为 0，则不创建重复图案。默认值为 0.0。

*csys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定局部坐标系。如果 *csys*=`None`，则使用全局坐标系。当查询此成员时，它返回一个 Int。默认值为 `None`。

*masterPoint*

`None` 或 [Region](pt01ch45pyo03.md) 对象，指定当 *masterPointDetermination* 为 SPECIFY 时使用的主点。默认值为 `None`。

*masterPointDetermination*

一个 SymbolicConstant，指定确定主节点的规则。可能的值为 MAXIMUM、MINIMUM 和 SPECIFY。默认值为 MAXIMUM。

*presumeFeasibleRegionAtStart*

一个布尔值，指定在第一个设计循环中是否忽略几何约束。默认值为 ON。

*tolerance1*

一个 Float，指定 1 方向的几何公差。默认值为 0.01。

*tolerance2*

一个 Float，指定 2 方向的几何公差。默认值为 0.01。

*tolerance3*

一个 Float，指定 3 方向的几何公差。默认值为 0.01。

**返回值**

ShapeRotationalSymmetry 对象。

**异常**

无。

### 36.19.2 setValues(...)

此方法修改 ShapeRotationalSymmetry 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [ShapeRotationalSymmetry](pt01ch36pyo19.md#ker-shaperotationalsymmetry-shaperotationalsymmetry-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 36.19.3 成员

ShapeRotationalSymmetry 对象具有与 [ShapeRotationalSymmetry](pt01ch36pyo19.md#ker-shaperotationalsymmetry-shaperotationalsymmetry-pyc) 方法的参数名称和描述相同的成员。
