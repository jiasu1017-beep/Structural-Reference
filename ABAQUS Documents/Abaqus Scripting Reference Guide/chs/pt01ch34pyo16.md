# 34.15 OdbInstance 对象

部件实例是装配中部件的使用。

**访问**

```
import odbAccess
session.odbs[*name*].rootAssembly.instances[*name*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance
```

### 34.15.1 Instance(...)

此方法从 [OdbPart](pt01ch34pyo19.md) 对象创建 OdbInstance 对象。

**路径**

```
session.odbs[*name*].rootAssembly.Instance
```

**必要参数**

*name*

一个字符串，指定实例名称。

*object*

一个 [OdbPart](pt01ch34pyo19.md) 对象。

**可选参数**

*localCoordSystem*

三个浮点数序列的序列，指定部件实例在全局笛卡尔坐标系中的旋转和平移。前三个序列指定以其中心在原点的新局部坐标系。
- 第一个序列指定 1 轴上的一点。
- 第二个序列指定 2 轴上的一点。
- 第三个序列指定 3 轴上的一点。

第四个序列指定局部坐标系从原点到其预期位置的平移。

例如，以下序列将部件沿 *X* 方向移动 10 个单位，不旋转：

```
localCoordSystem = ((1, 0, 0), (0, 1, 0),
                                 (0, 0, 1), (10, 0, 0))
```

以下序列将部件沿 *X* 方向移动 5 个单位并旋转：

```
localCoordSystem = ((0, 1, 0), (1, 0, 0),
                                 (0, 0, 1), (5, 0, 0))
```

将包含以下两点的部件转换
```
Pt1= (1,0,0) 
Pt2= (2,0,0) 
```
为
```
Pt1 = (0, 6, 0) 
Pt2 = (0, 7, 0)                      
```

**返回值**

OdbInstance 对象。

**异常**

InvalidNameError。

### 34.15.2 assignBeamOrientation(...)

此方法为部件实例的区域分配梁截面方向。

**必要参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md)，指定实例上的一个区域。

*method*

一个 SymbolicConstant，指定分配方法。当前仅支持 N1_COSINES。

*vector*

三个浮点数序列，指定梁截面近似局部 ![](../graphics/ker_eqn00406.gif) 方向。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 34.15.3 assignMaterialOrientation(...)

此方法为部件实例的区域分配材料方向。

**必要参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md)，指定实例上的一个区域。

*localCsys*

一个 [OdbDatumCsys](pt01ch34pyo13.md) 对象，指定局部坐标系，或 `None`，表示全局坐标系。

**可选参数**

*axis*

一个 SymbolicConstant，指定圆柱形或球形基准坐标系的轴，围绕该轴应用额外旋转。对于壳，此轴也是壳法线。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle*

一个 Float，指定额外旋转的角度。默认值为 0.0。

*stackDirection*

一个 SymbolicConstant，指定材料的堆叠或厚度方向。可能的值为 STACK_1、STACK_2、STACK_3 和 STACK_ORIENTATION。默认值为 STACK_3。

**返回值**

无

**异常**

无。

### 34.15.4 assignRebarOrientation(...)

此方法为部件实例的区域分配钢筋参考方向。

**必要参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md)，指定实例上的一个区域。

*localCsys*

一个 [OdbDatumCsys](pt01ch34pyo13.md) 对象，指定局部坐标系，或 `None`，表示全局坐标系。

**可选参数**

*axis*

一个 SymbolicConstant，指定圆柱形或球形基准坐标系的轴，围绕该轴应用额外旋转。对于壳，此轴也是壳法线。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle*

一个 Float，指定额外旋转的角度。默认值为 0.0。

**返回值**

无

**异常**

无。

### 34.15.5 getElementFromLabel(...)

此方法用于从实例对象中检索具有特定标签的单元。

**必要参数**

*label*

一个整数，指定单元标签。

**可选参数**

无。

**返回值**

一个 [OdbMeshElement](pt01ch34pyo17.md) 对象。

**异常**

如果不存在具有指定标签的单元：

```
OdbError: Invalid element label
```

### 34.15.6 getNodeFromLabel(...)

此方法用于从实例对象中检索具有特定标签的节点。

**必要参数**

*label*

一个整数，指定节点标签。

**可选参数**

无。

**返回值**

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象。

**异常**

如果不存在具有指定标签的节点：

```
OdbError: Invalid node label
```

### 34.15.7 assignSection(...)

此方法用于为实例上的区域分配截面。

**必要参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md)，指定实例上的一个区域。

*section*

一个 [Section](pt01ch46pyo01.md) 对象。

**可选参数**

无。

**返回值**

无

**异常**

如果 *region* 不是元素集：

```
OdbError: Section assignment requires element set.
```

如果元素集不是来自当前实例：

```
OdbError: Section assignment requires element set from this part instance.
```

### 34.15.8 AnalyticRigidSurf2DPlanar(...)

此方法用于在实例上定义二维 [AnalyticSurface](pt01ch34pyo02.md) 对象。

**必要参数**

*name*

解析曲面的名称。

*profile*

[AnalyticSurfaceSegment](pt01ch34pyo03.md) 对象序列或 [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md) 对象。

**可选参数**

*filletRadius*

一个 Double，指定平滑相邻段之间不连续性的曲率半径。默认值为 0.0。

**返回值**

无

**异常**

如果关联的 [OdbPart](pt01ch34pyo19.md) 类型为 THREE_D：

```
OdbError: 2D-Planar Analytic Rigid Surface can be defined only if the instance is of type                             TWO_D_PLANAR                            or                             AXISYMMETRIC.                         
```

### 34.15.9 AnalyticRigidSurfExtrude(...)

此方法用于在实例上定义三维圆柱形 [AnalyticSurface](pt01ch34pyo02.md)。

**必要参数**

*name*

解析曲面的名称。

*profile*

[AnalyticSurfaceSegment](pt01ch34pyo03.md) 对象序列或 [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md) 对象。

**可选参数**

*filletRadius*

一个 Double，指定平滑相邻段之间不连续性的曲率半径。默认值为 0.0。

*localCoordData*

浮点数序列的序列，指定用于定义局部坐标系的点的全局坐标。

**返回值**

无

**异常**

如果关联的 [OdbPart](pt01ch34pyo19.md) 类型不是 THREE_D：

```
OdbError:  Analytic Rigid Surface of type                             CYLINDER                            can be defined only if the instance is of type                             THREE_D.                         
```

### 34.15.10 AnalyticRigidSurfRevolve(...)

此方法用于在实例上定义三维旋转 [AnalyticSurface](pt01ch34pyo02.md)。

**必要参数**

*name*

解析曲面的名称。

*profile*

[AnalyticSurfaceSegment](pt01ch34pyo03.md) 对象序列或 [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md) 对象。

**可选参数**

*filletRadius*

一个 Double，指定平滑相邻段之间不连续性的曲率半径。默认值为 0.0。

*localCoordData*

浮点数序列的序列，指定用于定义局部坐标系的点的全局坐标。

**返回值**

无

**异常**

如果关联的 [OdbPart](pt01ch34pyo19.md) 类型不是 THREE_D：

```
OdbError:  Analytic Rigid Surface of type                             REVOLUTION                            can be defined only if the instance is of type                             THREE_D.                         
```

### 34.15.11 RigidBody(...)

此方法在实例上定义一个 [OdbRigidBody](pt01ch34pyo21.md)。

**必要参数**

*referenceNode*

一个 [OdbSet](pt01ch34pyo23.md)，指定分配给刚体的参考节点。

**可选参数**

*position*

一个符号常量，指定是否由用户定义参考节点的位置。可能的值为 INPUT 和 CENTER_OF_MASS。默认值为 INPUT。

*isothermal*

一个布尔值，指定等温刚体。默认值为 OFF。此参数仅用于完全耦合的热应力分析。

*elset*

一个 [OdbSet](pt01ch34pyo23.md)，指定分配给刚体的元素集。

*pinNodes*

一个 [OdbSet](pt01ch34pyo23.md)，指定分配给刚体的销钉型节点。

*tieNodes*

一个 [OdbSet](pt01ch34pyo23.md)，指定分配给刚体的绑定型节点。

**返回值**

无

**异常**

如果 *referenceNode* 不是节点集：

```
OdbError: Rigid body definition requires a node set.
```

### 34.15.12 getNodeFromLabel(...)

此方法用于从实例对象中检索具有特定标签的节点。

**必要参数**

*label*

一个整数，指定节点标签。

**可选参数**

无。

**返回值**

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象。

**异常**

如果不存在具有指定标签的节点：

```
OdbError: Invalid node label
```

### 34.15.13 getNodeFromLabel(...)

此方法用于从实例对象中检索具有特定标签的节点。

**必要参数**

*label*

一个整数，指定节点标签。

**可选参数**

无。

**返回值**

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象。

**异常**

如果不存在具有指定标签的节点：

```
OdbError: Invalid node label
```

### 34.15.14 成员

OdbInstance 对象可以具有以下成员：

*name*

一个字符串，指定实例名称。

*type*

一个 SymbolicConstant，指定 [Part](pt01ch37pyo01.md) 对象的类型。当前仅支持 DEFORMABLE_BODY。

*embeddedSpace*

一个 SymbolicConstant，指定 [Part](pt01ch37pyo01.md) 对象的维度。可能的值为 THREE_D、TWO_D_PLANAR、AXISYMMETRIC 和 UNKNOWN_DIMENSION。

*resultState*

一个 SymbolicConstant，指定由分析修改的实例状态。此成员仅在 Instance 是 RootAssemblyState 树的一部分时存在。可能的值为：
- PROPAGATED，指定该值与前一帧或原始 rootAssembly 相同。
- MODIFIED，指定实例的几何形状在此帧已更改。

默认值为 PROPAGATED。

*nodes*

一个 [OdbMeshNodeArray](pt01ch34pyo18.md) 对象。

*elements*

一个 [OdbMeshElementArray](pt01ch34pyo17.md) 对象。

*nodeSets*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定节点集。

*elementSets*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定元素集。

*surfaces*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定曲面。

*sectionAssignments*

一个 [SectionAssignmentArray](pt01ch44pyo01.md) 对象。

*rigidBodies*

一个 [OdbRigidBodyArray](pt01ch34pyo21.md) 对象。

*beamOrientations*

一个 [BeamOrientationArray](pt01ch34pyo04.md) 对象。

*materialOrientations*

一个 [MaterialOrientationArray](pt01ch44pyo04.md) 对象。

*rebarOrientations*

一个 [RebarOrientationArray](pt01ch34pyo25.md) 对象。

*analyticSurface*

一个 [AnalyticSurface](pt01ch34pyo02.md) 对象，指定在实例上定义的解析曲面。
