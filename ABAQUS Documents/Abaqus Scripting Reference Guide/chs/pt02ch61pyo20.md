# 61.20 OdbPart 对象

OdbPart 对象与内核 Part 对象类似，包含节点和元素，但没有几何体。

**访问**

```
odb.parts()[*name*]
```

### 61.20.1 Part(...)

此方法创建一个 OdbPart 对象。节点和元素稍后添加到此对象。

**路径**

```
odb.Part
```

**原型**

```
odb_Part&
Part(const odb_String& name,
     odb_Enum::odb_DimensionEnum embeddedSpace,
     odb_Enum::odb_PartTypeEnum type);
```

**必需参数**

*name*

一个 odb_String，指定部件名称。

*embeddedSpace*

一个 odb_Enum::odb_DimensionEnum，指定 [OdbPart](pt02ch61pyo20.md) 对象的维度。可能的值为 odb_Enum::THREE_D、odb_Enum::TWO_D_PLANAR 和 odb_Enum::AXISYMMETRIC。

*type*

一个 odb_Enum::odb_PartTypeEnum，指定 [OdbPart](pt02ch61pyo20.md) 对象的类型。可能的值为 odb_Enum::DEFORMABLE_BODY 和 odb_Enum::ANALYTIC_RIGID_SURFACE。

**可选参数**

无。

**返回值**

一个 OdbPart 对象。

**异常**

无。

### 61.20.2 addElements(...)

此方法使用元素标签和节点连通性向 OdbPart 对象添加元素。

**警告：**添加不按标签升序排列的元素可能导致 Abaqus/Viewer 错误地绘制轮廓。

**原型**

```
void
addElements(const odb_SequenceInt& labels,
            const odb_SequenceSequenceInt& connectivity,
            const odb_String& type,
            const odb_String& elementSetName,
            const odb_SectionCategory& sectionCategory);
```

**必需参数**

*labels*

一个 odb_SequenceInt，指定元素标签。

*connectivity*

一个 odb_SequenceSequenceInt，指定节点连通性。

*type*

一个 String，指定元素类型。

**可选参数**

*elementSetName*

一个 String，指定此元素集的名称。默认值为空字符串。

*sectionCategory*

一个 [SectionCategory](pt02ch61pyo27.md) 对象，用于此元素集。

**返回值**

无

**异常**

无。

### 61.20.3 addNodes(...)

此方法使用节点标签和坐标向 OdbPart 对象添加节点。

**警告：**添加不按标签升序排列的节点可能导致 Abaqus/Viewer 错误地绘制轮廓。

**原型**

```
void
addNodes(const odb_SequenceInt& labels,
         const odb_SequenceSequenceFloat& coordinates,
         const odb_String& nodeSetName);
```

**必需参数**

*labels*

一个 odb_SequenceInt，指定节点标签。

*coordinates*

一个 odb_SequenceSequenceFloat，指定节点坐标。

**可选参数**

*nodeSetName*

一个 String，指定此节点集的名称。默认值为 None。

**返回值**

无

**异常**

无。

### 61.20.4 assignBeamOrientation(...)

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

### 61.20.5 assignMaterialOrientation(...)

此方法为部件实例的区域分配材料方向。

**原型**

```
void
assignMaterialOrientation(const odb_Set& region,
             const odb_DatumCsys& localCSys,
             odb_Enum::odb_AxisEnum axis,
             float angle,
             odb_Enum::odb_StackDirectionEnum stackDirection);
```

**必需参数**

*region*

一个 [OdbSet](pt02ch61pyo24.md)，指定实例上的区域。

*localCSys*

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

### 61.20.6 assignRebarOrientation(...)

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

### 61.20.7 getElementFromLabel(...)

此方法用于从部件对象中检索具有特定标签的元素。

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

### 61.20.8 getNodeFromLabel(...)

此方法用于从部件对象中检索具有特定标签的节点。

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

### 61.20.9 AnalyticRigidSurf2DPlanar(...)

此方法用于在部件对象上定义二维 [AnalyticSurface](pt02ch61pyo02.md) 对象。

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

如果 OdbPart 类型为 THREE_D：

```
OdbError: 2D-Planar Analytic Rigid Surface can be defined only if the part is of type                             TWO_D_PLANAR                            or                             AXISYMMETRIC.                         
```

### 61.20.10 AnalyticRigidSurfExtrude(...)

此方法用于在部件对象上定义三维圆柱形 [AnalyticSurface](pt02ch61pyo02.md)。

**原型**

```
void
AnalyticRigidSurfExtrude(const odb_String& name,
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

如果 OdbPart 类型不是 THREE_D：

```
OdbError:  Analytic Rigid Surface of type                            CYLINDER                            can be defined only if the part is of type                             THREE_D.                         
```

### 61.20.11 AnalyticRigidSurfRevolve(...)

此方法用于在部件对象上定义三维旋转 [AnalyticSurface](pt02ch61pyo02.md)。

**原型**

```
void
AnalyticRigidSurfRevolve(const odb_String& name,
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

如果 OdbPart 类型不是 THREE_D：

```
OdbError:  Analytic Rigid Surface of type                             REVOLUTION                            can be defined only if the part is of type                             THREE_D.                         
```

### 61.20.12 RigidBody(...)

此方法在部件对象上定义一个 [OdbRigidBody](pt02ch61pyo22.md)。

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

### 61.20.13 成员

OdbPart 对象具有与 [Part](pt02ch61pyo20.md#ker-odbpart-part-cpp) 方法参数相同名称和描述的成员。

此外，OdbPart 对象可以具有以下成员：

**原型**

```
odb_String name() const;
               odb_Enum::odb_DimensionEnum embeddedSpace() const;
               odb_Enum::odb_PartTypeEnum type() const;
               odb_Node& nodes(int index) const;
               odb_SequenceNode& nodes() const;
               odb_Element& elements(int index) const;
               odb_SequenceElement& elements() const;
               odb_SetRepository& nodeSets() const;
               odb_SetRepository& elementSets() const;
               odb_SetRepository& surfaces() const;
               odb_SequenceSectionAssignment sectionAssignments() const;
               odb_SequenceBeamOrientation beamOrientations() const;
               odb_SequenceMaterialOrientation materialOrientations() const;
               odb_SequenceRebarOrientation rebarOrientations() const;
               odb_SequenceRigidBody rigidBodies() const;
               bool hasAnalyticSurface() const;
               odb_AnalyticSurface analyticSurface() const;
```

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

*beamOrientations*

[BeamOrientation](pt02ch61pyo04.md) 对象的序列。

*materialOrientations*

[MaterialOrientation](#ker-materialorientation-cpp) 对象的序列。

*rebarOrientations*

[RebarOrientation](pt02ch61pyo26.md) 对象的序列。

*rigidBodies*

[OdbRigidBody](pt02ch61pyo22.md) 对象的序列。

*analyticSurface*

一个 [AnalyticSurface](pt02ch61pyo02.md) 对象，指定在实例上定义的解析曲面。
