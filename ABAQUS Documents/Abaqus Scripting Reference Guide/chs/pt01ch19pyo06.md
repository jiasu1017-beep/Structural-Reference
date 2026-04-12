# 19.6 DiscreteFastener 对象









DiscreteFastener 对象定义离散紧固件。

DiscreteFastener 对象派生自 [Fastener](pt01ch19pyo07.md) 对象。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.fasteners[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.fasteners[*name*]
```

### 19.6.1 DiscreteFastener(...)

此方法创建 DiscreteFastener 对象。尽管构造函数可用于部件和装配，但 DiscreteFastener 对象目前仅在装配下支持。

**路径**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.DiscreteFastener
mdb.models[*name*].rootAssembly.engineeringFeatures.DiscreteFastener
```

**必需参数**

*name*

一个 String，指定存储库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用紧固件的区域。

*influenceRadius*

SymbolicConstant WHOLE_SURFACE 或一个 Float，指定耦合影响半径。

**可选参数**

*ur1*

一个 Boolean，指定是否约束关于 1 方向的旋转位移分量。默认值为 ON。

*ur2*

一个 Boolean，指定是否约束关于 2 方向的旋转位移分量。默认值为 ON。

*ur3*

一个 Boolean，指定是否约束关于 3 方向的旋转位移分量。默认值为 ON。

*coupling*

一个 SymbolicConstant，指定用于将每个附着点的位移和旋转耦合到紧固点影响半径内表面节点平均运动的耦合方法。可能的值为 CONTINUUM 和 STRUCTURAL。默认值为 CONTINUUM。

*weightingMethod*

一个 SymbolicConstant，指定用于加权影响半径内表面节点位移对紧固点运动贡献的加权方案。UNIFORM、LINEAR、QUADRATIC 和 CUBIC 分别表示均匀、线性递减、二次多项式递减和三次多项式单调递减权重分布。可能的值为 UNIFORM、LINEAR、QUADRATIC 和 CUBIC。默认值为 UNIFORM。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定紧固件耦合的局部坐标系。如果 *localCsys*=`None`，则在全局坐标系中定义耦合。查询此成员时，它返回一个 Int。默认值为 `None`。

**返回值**

一个 DiscreteFastener 对象。

**异常**

无。

### 19.6.2 setValues(...)

此方法修改 DiscreteFastener 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DiscreteFastener](pt01ch19pyo06.md#ker-discretefastener-discretefastener-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 19.6.3 成员

DiscreteFastener 对象具有与 [DiscreteFastener](pt01ch19pyo06.md#ker-discretefastener-discretefastener-pyc) 方法的参数相同的名称和描述的成员。

此外，DiscreteFastener 对象还有以下成员：

*suppressed*

一个 Boolean，指定紧固件是否被抑制。默认值为 OFF。

### 19.6.4 对应的分析关键字

| [*COUPLING](../key/key-link.md#usb-kws-mcoupling), [*DISTRIBUTING](../key/key-link.md#usb-kws-mdistributing) |
| --- |





