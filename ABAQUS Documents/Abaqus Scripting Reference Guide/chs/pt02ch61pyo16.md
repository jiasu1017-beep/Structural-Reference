# 61.16 OdbInstance 对象

部件实例是部件在装配中的使用。

**访问**

```
odb.rootAssembly().instances()[*name*]
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()
```

### 61.16.1 Instance(...)

此方法从 [OdbPart](pt02ch61pyo20.md) 对象创建 OdbInstance 对象。

**路径**

```
odb.rootAssembly().Instance
```

**原型**

```
odb_Instance&
Instance(const odb_String& name,
         const odb_Part& object,
         const odb_SequenceSequenceFloat& localCoordSystem);
```

**必需参数**

*name*

一个 odb_String，指定实例名称。

*object*

一个 [OdbPart](pt02ch61pyo20.md) 对象。

**可选参数**

*localCoordSystem*

一个 odb_SequenceSequenceFloat，指定部件实例在全局 Cartesian 坐标系中的旋转和平移。前三个序列指定以其中心在原点的新局部坐标系。
- 第一个序列指定 1 轴上的一点。
- 第二个序列指定 2 轴上的一点。
- 第三个序列指定 3 轴上的一点。

第四个序列指定局部坐标系从原点到其预期位置的平移。

例如，以下序列将部件沿 *X* 方向移动 10 个单位，不旋转：

```
localCoordSystem = ((1, 0, 0), (0, 1, 0),
                                 (0, 0, 1), (10, 0, 0))
```

以下序列将部件沿 *X* 方向移动 5 个单位，有旋转：

```
localCoordSystem = ((0, 1, 0), (1, 0, 0),
                                 (0, 0, 1), (5, 0, 0))
```

将包含以下两点的部件转换

```
                                 Pt1= (1,0,0) 
                                 Pt2= (2,0,0) 
```

到

```
                                 Pt1 = (0, 6, 0) 
                                 Pt2 = (0, 7, 0)                      
```

**返回值**

一个 OdbInstance 对象。

**异常**

InvalidNameError。

### 61.16.2 assignBeamOrientation(...)

此方法为部件实例的区域分配梁截面方向。

**原型**

```
void
assignBeamOrientation(const odb_Set& region,
                  odb_Enum::odb_OrientationMethodEnum method,
                  const odb_SequenceFloat& vector);
```

**必需参数**

*region*

一个 [OdbSet](pt02ch61pyo24.md)，指定实例上的区域。

*method*

一个 odb_Enum::odb_OrientationMethodEnum，指定分配方法。当前仅支持 odb_Enum::N1_COSINES。

*vector*

一个 odb_SequenceFloat，指定梁截面的大致局部 ![](../graphics/ker_eqn00406.gif) 方向。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 61.16.3 assignMaterialOrientation(...)

此方法为部件实例的区域分配材料方向。

**原型**

```
void
assignMaterialOrientation(const odb_Set& region,
             const odb_DatumCsys& localCsys,
             odb_Enum::odb_AxisEnum axis,
             float angle,
             odb_Enum::odb_StackDirectionEnum stackDirection);
```

**必需参数**

*region*

一个 [OdbSet](pt02ch61pyo24.md)，指定实例上的区域。

*localCsys*

一个 [OdbDatumCsys](pt02ch61pyo14.md) 对象，指定局部坐标系，或 `None`，表示全局坐标系。

**可选参数**

*axis*

一个 odb_Enum::odb_AxisEnum，指定圆柱形或球形基准坐标系的轴，关于该轴应用附加旋转。对于壳单元，此轴也是壳法线。可能的值为 odb_Enum::AXIS_1、odb_Enum::AXIS_2 和 odb_Enum::AXIS_3。默认值为 odb_Enum::AXIS_1。

*angle*

一个 Float，指定附加旋转的角度。默认值为 0.0。

*stackDirection*

一个 odb_Enum::odb_StackDirectionEnum，指定材料的堆叠或厚度方向。可能的值为 odb_Enum::STACK_1、odb_Enum::STACK_2、odb_Enum::STACK_3 和 odb_Enum::STACK_ORIENTATION。默认值为 odb_Enum::STACK_3。

**返回值**

无

**异常**

无。

### 61.16.4 assignRebarOrientation(...)

此方法为部件实例的区域分配钢筋参考方向。

**原型**

```
void
assignRebarOrientation(const odb_Set& region,
                       const odb_DatumCsys& localCsys,
                       odb_Enum::odb_AxisEnum axis,
                       float angle);
```

**必需参数**

*region*

一个 [OdbSet](pt02ch61pyo24.md)，指定实例上的区域。

*localCsys*

一个 [OdbDatumCsys](pt02ch61pyo14.md) 对象，指定局部坐标系，或 `None`，表示全局坐标系。

**可选参数**

*axis*

一个 odb_Enum::odb_AxisEnum，指定圆柱形或球形基准坐标系的轴，关于该轴应用附加旋转。对于壳单元，此轴也是壳法线。可能的值为 odb_Enum::AXIS_1、odb_Enum::AXIS_2 和 odb_Enum::AXIS_3。默认值为 odb_Enum::AXIS_1。

*angle*

一个 Float，指定附加旋转的角度。默认值为 0.0。

**返回值**

无

**异常**

无。

### 61.16.5 getElementFromLabel(...)

此方法用于从实例对象中检索具有特定标签的元素。

**原型**

```
odb_Element
getElementFromLabel(int label);
```

**必需参数**

*label*

一个 Int，指定元素标签。

**可选参数**

无。

**返回值**

一个 [OdbMeshElement](pt02ch61pyo18.md) 对象。

**异常**

如果不存在具有指定标签的元素：

```
OdbError: Invalid element label
```

### 61.16.6 getNodeFromLabel(...)

此方法用于从实例对象中检索具有特定标签的节点。

**原型**

```
odb_Node
getNodeFromLabel(int label);
```

**必需参数**

*label*

一个 Int，指定节点标签。

**可选参数**

无。

**返回值**

一个 [OdbMeshNode](pt02ch61pyo19.md) 对象。

**异常**

如果不存在具有指定标签的节点：

```
OdbError: Invalid node label
```

### 61.16.7 assignSection(...)

此方法用于为实例上的区域分配截面。

**原型**

```
void
assignSection(const odb_Set& region,
              const odb_section& section);
```

**必需参数**

*region*

一个 [OdbSet](pt02ch61pyo24.md)，指定实例上的区域。

*section*

一个 [Section](pt02ch63pyo01.md) 对象。

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

### 61.16.8 AnalyticRigidSurf2DPlanar(...)

此方法用于在实例上定义二维 [AnalyticSurface](pt02ch61pyo02.md) 对象。

**原型**

```
void
AnalyticRigidSurf2DPlanar(const odb_String& name,
           const odb_SequenceAnalyticSurfaceSegment& profile,
           double filletRadius);
```

**必需参数**

*name*

解析曲面的名称。

*profile*

[AnalyticSurfaceSegment](pt02ch61pyo03.md) 对象序列或 [OdbSequenceAnalyticSurfaceSegment](pt02ch61pyo23.md) 对象。

**可选参数**

*filletRadius*

一个 Double，指定用于平滑相邻段之间不连续的曲率半径。默认值为 0.0。

**返回值**

无

**异常**

如果与部件实例关联的 [OdbPart](pt02ch61pyo20.md) 类型为 THREE_D：

```
OdbError: 2D-Planar Analytic Rigid Surface can be defined only if the instance is of type                             TWO_D_PLANAR                            or                             AXISYMMETRIC.                         
```

### 61.16.9 AnalyticRigidSurfExtrude(...)

此方法用于在实例上定义三维圆柱形 [AnalyticSurface](pt02ch61pyo02.md)。

**原型**

```
void
AnalyticRigidSurfExtrude(const odb_String& name,
           const odb_SequenceAnalyticSurfaceSegment& profile,
           double filletRadius,
           const odb_SequenceSequenceFloat& localCoordData);
```

**必需参数**

*name*

解析曲面的名称。

*profile*

[AnalyticSurfaceSegment](pt02ch61pyo03.md) 对象序列或 [OdbSequenceAnalyticSurfaceSegment](pt02ch61pyo23.md) 对象。

**可选参数**

*filletRadius*

一个 Double，指定用于平滑相邻段之间不连续的曲率半径。默认值为 0.0。

*localCoordData*

一个 odb_SequenceSequenceFloat，指定用于定义局部坐标系的点的全局坐标。

**返回值**

无

**异常**

如果与部件实例关联的 [OdbPart](pt02ch61pyo20.md) 类型不是 THREE_D：

```
OdbError:  Analytic Rigid Surface of type                             CYLINDER                            can be defined only if the instance is of type                             THREE_D.                         
```

### 61.16.10 AnalyticRigidSurfRevolve(...)

此方法用于在实例上定义三维旋转 [AnalyticSurface](pt02ch61pyo02.md)。

**原型**

```
void
AnalyticRigidSurfRevolve(const odb_String& name,
           const odb_SequenceAnalyticSurfaceSegment& profile,
           double filletRadius,
           const odb_SequenceSequenceFloat& localCoordData);
```

**必需参数**

*name*

解析曲面的名称。

*profile*

[AnalyticSurfaceSegment](pt02ch61pyo03.md) 对象序列或 [OdbSequenceAnalyticSurfaceSegment](pt02ch61pyo23.md) 对象。

**可选参数**

*filletRadius*

一个 Double，指定用于平滑相邻段之间不连续的曲率半径。默认值为 0.0。

*localCoordData*

一个 odb_SequenceSequenceFloat，指定用于定义局部坐标系的点的全局坐标。

**返回值**

无

**异常**

如果与部件实例关联的 [OdbPart](pt02ch61pyo20.md) 类型不是 THREE_D：

```
OdbError:  Analytic Rigid Surface of type                             REVOLUTION                            can be defined only if the instance is of type                             THREE_D.                         
```

### 61.16.11 RigidBody(...)

此方法在实例上定义一个 [OdbRigidBody](pt02ch61pyo22.md)。

**原型**

```
void
RigidBody(const odb_Set& referenceNode,
          odb_Enum::odb_PositionEnum position,
          bool isothermal,
          const odb_Set& elset,
          const odb_Set& pinNodes,
          const odb_Set& tieNodes);
```

**必需参数**

*referenceNode*

一个 [OdbSet](pt02ch61pyo24.md)，指定分配给刚体的参考节点。

**可选参数**

*position*

一个符号常数，指定是否由用户定义参考节点的位置。可能的值为 odb_Enum::INPUT 和 odb_Enum::CENTER_OF_MASS。默认值为 odb_Enum::INPUT。

*isothermal*

一个 Boolean，指定等温刚体。默认值为 false。此参数仅用于完全耦合的热应力分析。

*elset*

一个 [OdbSet](pt02ch61pyo24.md)，指定分配给刚体的元素集。

*pinNodes*

一个 [OdbSet](pt02ch61pyo24.md)，指定分配给刚体的销钉型节点。

*tieNodes*

一个 [OdbSet](pt02ch61pyo24.md)，指定分配给刚体的绑定型节点。

**返回值**

无

**异常**

如果 *referenceNode* 不是节点集：

```
OdbError: Rigid body definition requires a node set.
```

### 61.16.12 getNodeFromLabel(...)

此方法用于从实例对象中检索具有特定标签的节点。

**原型**

```
odb_Node
getNodeFromLabel(int label);
```

**必需参数**

*label*

一个 Int，指定节点标签。

**可选参数**

无。

**返回值**

一个 [OdbMeshNode](pt02ch61pyo19.md) 对象。

**异常**

如果不存在具有指定标签的节点：

```
OdbError: Invalid node label
```

### 61.16.13 getNodeFromLabel(...)

此方法用于从实例对象中检索具有特定标签的节点。

**原型**

```
odb_Node
getNodeFromLabel(int label);
```

**必需参数**

*label*

一个 Int，指定节点标签。

**可选参数**

无。

**返回值**

一个 [OdbMeshNode](pt02ch61pyo19.md) 对象。

**异常**

如果不存在具有指定标签的节点：

```
OdbError: Invalid node label
```

### 61.16.14 nodesLabelsFromNodeTypeFace(...)

给定一个定义元素连通性的整数序列，此方法用于根据元素类型检索附加到元素指定面的节点序列。

**原型**

```
odb_SequenceInt
nodesLabelsFromNodeTypeFace(const odb_SequenceInt& elementNodeLabels,
               const odb_String& elementType,
               odb_Enum::odb_ElementFaceEnumEnum elementFace);
```

**必需参数**

*elementNodeLabels*

一个 Int 序列，指定定义整个元素的连通性的节点标签。

*elementType*

一个字符串，指定提供连通性的元素类型。

*elementFace*

一个 SymbolicConstant，指定需要节点标签的元素面。

**可选参数**

无。

**返回值**

一个 Int 序列，指定对应于所需元素面的节点标签。

**异常**

如果指定的面对于元素类型无效：

```
OdbError: Invalid face
```

### 61.16.15 成员

OdbInstance 对象可以具有以下成员：

**原型**

```
odb_String name() const;
               odb_Enum::odb_DimensionEnum embeddedSpace() const;
               odb_Enum::odb_PartTypeEnum type() const;
               odb_Node nodes(int i) const;
               odb_SequenceNode& nodes() const;
               odb_Element elements(int i) const;
               odb_SequenceElement& elements() const;
               odb_SetRepository& nodeSets() const;
               odb_SetRepository& elementSets() const;
               odb_SetRepository& surfaces() const;
               odb_SequenceSectionAssignment sectionAssignments()\
                   const;
               odb_SequenceBeamOrientation beamOrientations() \
                   const;
               odb_SequenceMaterialOrientation materialOrientations() \
                   const;
               odb_SequenceRebarOrientation rebarOrientations() \
                   const;
               odb_SequenceRigidBody rigidBodies() const;
               bool hasAnalyticSurface() const;
               odb_AnalyticSurface analyticSurface() const;
```

*name*

一个 odb_String，指定实例名称。

*type*

一个 odb_Enum::odb_PartTypeEnum，指定 [OdbPart](pt02ch61pyo20.md) 对象的类型。当前仅支持 odb_Enum::DEFORMABLE_BODY。

*embeddedSpace*

一个 odb_Enum::odb_DimensionEnum，指定 [OdbPart](pt02ch61pyo20.md) 对象的维度。可能的值为 odb_Enum::THREE_D、odb_Enum::TWO_D_PLANAR、odb_Enum::AXISYMMETRIC 和 odb_Enum::UNKNOWN_DIMENSION。

*resultState*

一个 odb_Enum::odb_ResultStateEnum，指定实例被分析修改的状态。此成员仅在实例是 RootAssemblyState 树的一部分时存在。可能的值为：
- odb_Enum::PROPAGATED，指定该值与前一帧或原始 rootAssembly 相同。
- odb_Enum::MODIFIED，指定实例的几何形状在此帧已被修改。

默认值为 odb_Enum::PROPAGATED。

*nodes*

[OdbMeshNode](pt02ch61pyo19.md) 对象的序列。

*elements*

[OdbMeshElement](pt02ch61pyo18.md) 对象的序列。

*nodeSets*

[OdbSet](pt02ch61pyo24.md) 对象（指定节点集）的存储库。

*elementSets*

[OdbSet](pt02ch61pyo24.md) 对象（指定元素集）的存储库。

*surfaces*

[OdbSet](pt02ch61pyo24.md) 对象（指定表面）的存储库。

*sectionAssignments*

[SectionAssignment](pt02ch62pyo01.md) 对象的序列。

*rigidBodies*

[OdbRigidBody](pt02ch61pyo22.md) 对象的序列。

*beamOrientations*

[BeamOrientation](pt02ch61pyo04.md) 对象的序列。

*materialOrientations*

[MaterialOrientation](#ker-materialorientation-cpp) 对象的序列。

*rebarOrientations*

[RebarOrientation](pt02ch61pyo26.md) 对象的序列。

*analyticSurface*

一个 [AnalyticSurface](pt02ch61pyo02.md) 对象，指定在实例上定义的解析曲面。
