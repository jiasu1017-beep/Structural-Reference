# 19.11 PointFastener 对象









PointFastener 对象定义点紧固件。

PointFastener 对象派生自 [Fastener](pt01ch19pyo07.md) 对象。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.fasteners[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.fasteners[*name*]
```

### 19.11.1 PointFastener(...)

此方法创建 PointFastener 对象。尽管构造函数可用于部件和装配，但 PointFastener 对象目前仅在装配下支持。

**路径**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.PointFastener
mdb.models[*name*].rootAssembly.engineeringFeatures.PointFastener
```

**必需参数**

*name*

一个 String，指定存储库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用紧固件的区域。

*physicalRadius*

一个 Float，指定物理紧固件半径。

**可选参数**

*directionVector*

长度为 2 的 [VertexArray](pt01ch07pyo15.md) 对象，指定投影方向。不是通过 [Vertex](pt01ch07pyo15.md)，每个点可以由坐标元组指定。默认值为 None。

*targetSurfaces*

一个 [RegionArray](pt01ch45pyo03.md) 对象，指定要紧固的表面。默认值为 MODEL。

*ur1*

一个 Boolean，指定是否约束关于 1 方向的旋转位移分量。默认值为 ON。

*ur2*

一个 Boolean，指定是否约束关于 2 方向的旋转位移分量。默认值为 ON。

*ur3*

一个 Boolean，指定是否约束关于 3 方向的旋转位移分量。默认值为 ON。

*attachmentMethod*

一个 SymbolicConstant，指定用于定位附着点以附加紧固件的方法。可能的值为 FACETOFACE、EDGETOFACE、FACETOEDGE 和 EDGETOEDGE。默认值为 FACETOFACE。

*influenceRadius*

SymbolicConstant DEFAULT 或一个 Float，指定从投影点在连接表面上的最大距离，位于该距离内的表面上的节点必须对投影点的运动有贡献。如果值为 DEFAULT，则从紧固件直径和表面面片长度计算半径。默认值为 DEFAULT。

*searchRadius*

SymbolicConstant DEFAULT 或一个 Float，指定从定位点开始，连接点必须位于其中的距离。默认值为 DEFAULT。

*maximumLayers*

SymbolicConstant ALL 或一个 Int，指定每个紧固件的最大层数。如果值为 ALL，则将为每个紧固件使用 searchRadius 内的最大可能层数。默认值为 ALL。

*coupling*

一个 SymbolicConstant，指定用于将每个附着点的位移和旋转耦合到紧固件投影点影响半径内表面节点平均运动的耦合方法。可能的值为 CONTINUUM 和 STRUCTURAL。默认值为 CONTINUUM。

*weightingMethod*

一个 SymbolicConstant，指定用于加权影响半径内表面节点位移对紧固件投影点运动贡献的加权方案。UNIFORM、LINEAR、QUADRATIC 和 CUBIC 分别表示均匀、线性递减、二次多项式递减和三次多项式单调递减权重分布。可能的值为 UNIFORM、LINEAR、QUADRATIC 和 CUBIC。默认值为 UNIFORM。

*additionalMass*

一个 Float，指定将分配到紧固件附着点的质量。默认值为 0.0。

*adjustOrientation*

一个 Boolean，指定是否调整 localCsys，使每个紧固件的局部 z 轴垂直于最接近该紧固件参考点的表面。默认值为 ON。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定局部坐标系。如果 *localCsys*=`None`，则使用全局坐标系。查询此成员时，它返回一个 Int。默认值为 `None`。

*connectionType*

一个 SymbolicConstant，指定紧固件连接类型。可能的值为 CONNECTOR 和 BEAM_MPC。默认值为 CONNECTOR。

*sectionName*

一个 String，指定分配给生成连接器的连接器截面。默认值为空字符串。

*connectorOrientationLocalCsys1*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定生成连接器中第一个连接点的局部坐标系。如果 *connectorOrientationLocalCsys1*=`None`，则 degrees of freedom 在全局坐标系中定义。查询此成员时，它返回一个 Int。默认值为 `None`。

*axis1*

一个 SymbolicConstant，指定附加旋转所围绕的基准坐标系轴。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle1*

一个 Float，指定生成连接器中第一个点的附加旋转角度。默认值为 0.0。

*orient2SameAs1*

一个 Boolean，指定生成连接器中第二个连接点是否使用与第一个点相同的局部坐标系、轴和角度。默认值为 ON。

*connectorOrientationLocalCsys2*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定生成连接器中第二个连接点的局部坐标系。如果 *connectorOrientationLocalCsys2*=`None`，则 degrees of freedom 在全局坐标系中定义。查询此成员时，它返回一个 Int。默认值为 `None`。

*axis2*

一个 SymbolicConstant，指定附加旋转所围绕的基准坐标系轴。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle2*

一个 Float，指定生成连接器中第二个点的附加旋转角度。默认值为 0.0。

*unsorted*

一个 Boolean，指定分析产品是否应按给定的未排序顺序保留 targetSurfaces，或按接近度排序它们以确定紧固点的连接性。默认值为 OFF。

**返回值**

一个 PointFastener 对象。

**异常**

无。

### 19.11.2 setValues(...)

此方法修改 PointFastener 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [PointFastener](pt01ch19pyo11.md#ker-pointfastener-pointfastener-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 19.11.3 成员

PointFastener 对象具有与 [PointFastener](pt01ch19pyo11.md#ker-pointfastener-pointfastener-pyc) 方法的参数相同的名称和描述的成员。

此外，PointFastener 对象还有以下成员：

*suppressed*

一个 Boolean，指定紧固件是否被抑制。默认值为 OFF。

### 19.11.4 对应的分析关键字

| [*FASTENER](../key/key-link.md#usb-kws-mfastener) |
| --- |





