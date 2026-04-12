# 61.13 OdbAssembly 对象

OdbAssembly 对象没有构造函数；当 [Odb](pt02ch61pyo01.md) 对象被创建时，Abaqus 会自动创建它。当创建 [Odb](pt02ch61pyo01.md) 对象时，Abaqus 会创建 *rootAssembly* 成员。

**访问**

```
odb.rootAssembly()
```

### 61.13.1 ConnectorOrientation(...)

此方法为连接器区域分配连接器方向。

**原型**

```
void
ConnectorOrientation(const odb_Set& region,
                     const odb_DatumCsys& csys1,
                     odb_Enum::odb_AxisEnum axis1,
                     float angle1,                     
                     const odb_DatumCsys& csys2,
                     odb_Enum::odb_AxisEnum axis2,
                     float angle2);
```

**必需参数**

*region*

一个 [OdbSet](pt02ch61pyo24.md)，指定区域。

*csys1*

一个 [OdbDatumCsys](pt02ch61pyo14.md) 对象，指定第一个连接器节点局部坐标系。

*axis1*

一个 odb_Enum::odb_AxisEnum，指定圆柱形或球形基准坐标系的轴，关于该轴应用第一个连接器节点的附加旋转。可能的值为 odb_Enum::AXIS_1、odb_Enum::AXIS_2 和 odb_Enum::AXIS_3。

*angle1*

一个 Float，指定关于第一个连接器节点轴的附加旋转角度。默认值为 0.0。

*csys2*

一个 [OdbDatumCsys](pt02ch61pyo14.md) 对象，指定第二个连接器节点局部坐标系。

*axis2*

一个 odb_Enum::odb_AxisEnum，指定圆柱形或球形基准坐标系的轴，关于该轴应用第二个连接器节点的附加旋转。可能的值为 odb_Enum::AXIS_1、odb_Enum::AXIS_2 和 odb_Enum::AXIS_3。

*angle2*

一个 Float，指定关于第二个连接器节点轴的附加旋转角度。

**返回值**

无

**异常**

如果 *region* 不是元素集：

```
OdbError: Connector orientation assignment requires element set.
```

### 61.13.2 ConnectorOrientation(...)

此方法为连接器区域分配连接器方向。

**原型**

```
        void
        ConnectorOrientation(const odb_Set& region,
        const odb_DatumCsys& csys1,
        odb_Enum::odb_AxisEnum axis1,
        float angle1,
        bool orient2sameAs1);
```

**必需参数**

*region*

一个 [OdbSet](pt02ch61pyo24.md)，指定区域。

*csys1*

一个 [OdbDatumCsys](pt02ch61pyo14.md) 对象，指定第一个连接器节点局部坐标系。

*axis1*

一个 odb_Enum::odb_AxisEnum，指定圆柱形或球形基准坐标系的轴，关于该轴应用第一个连接器节点的附加旋转。可能的值为 odb_Enum::AXIS_1、odb_Enum::AXIS_2 和 odb_Enum::AXIS_3。

*angle1*

一个 Float，指定关于第一个连接器节点轴的附加旋转角度。

**可选参数**

*orient2sameAs1*

一个 Boolean，指定是否为连接器的第二个节点使用相同的方向设置。默认值为 false。

**返回值**

无

**异常**

如果 *region* 不是元素集：

```
OdbError: Connector orientation assignment requires element set.
```

### 61.13.3 SectionAssignment(...)

此方法用于在实例上为区域分配截面。仅连接器截面可以在装配级别分配。

**原型**

```
void
SectionAssignment(const odb_Set& region,
                  const odb_section& section);
```

**必需参数**

*region*

一个 [OdbSet](pt02ch61pyo24.md)，指定区域。

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

### 61.13.4 addElements(...)

此方法用于使用在 OdbAssembly 和/或 [OdbInstance](pt02ch61pyo16.md) 级别定义的节点来定义元素。对于连接到地面的连接器元素，请在连通性中指定孤立的节点。地面节点的位置无法指定。这是一个限制。

**警告：**添加不按标签升序排列的元素可能导致 Abaqus/Viewer 错误地绘制轮廓。

**原型**

```
void
addElements(const odb_SequenceInt& labels,
            const odb_SequenceSequenceInt& connectivity,
            const odb_SequenceString& instanceNames,
            const odb_String& type,
            const odb_String& elementSetName,
            const odb_SectionCategory& sectionCategory);
```

**必需参数**

*labels*

一个 odb_SequenceInt，指定元素标签。

*connectivity*

一个 odb_SequenceSequenceInt，指定节点连通性。

*instanceNames*

一个 odb_SequenceString，指定节点连通性数组中每个节点的 instanceNames。如果节点在装配级别定义，则实例名称应为空字符串。

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

仅某些元素类型允许在装配级别。例如，连接器元素。

```
OdbError: Addition of this element type is not permitted at the assembly level
```

如果标签数组长度与连通性数据长度不匹配：

```
OdbError: Connectivity array must be provided for all element
```

### 61.13.5 addNodes(...)

此方法使用节点标签和坐标向 OdbAssembly 对象添加节点。

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

如果标签长度与坐标长度不匹配：

```
OdbError: Number of node labels and coordinates does not match
```

如果坐标数组宽度与装配维度不匹配：

```
OdbError: Node location specification does not correspond to part dimensions
```

### 61.13.6 sectionAssignments(...)

此方法用于检索截面分配。

**原型**

```
odb_SectionAssignment
sectionAssignments(int index);
```

**必需参数**

*index*

一个 Int，指定截面分配。

**可选参数**

无。

**返回值**

一个 [SectionAssignment](pt02ch62pyo01.md) 对象。

**异常**

无。

### 61.13.7 RigidBody(...)

此方法在装配上定义一个 [OdbRigidBody](pt02ch61pyo22.md)。

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

### 61.13.8 成员

OdbAssembly 对象可以具有以下成员：

**原型**

```
odb_InstanceRepository& instances();
               odb_SetRepository& nodeSets();
               odb_SetRepository& elementSets();
               odb_SetRepository& surfaces();
               odb_SequenceNode& nodes() const;
               odb_SequenceElement& elements() const;
               odb_DatumCsysRepository& datumCsyses();
               odb_SequenceSectionAssignment sectionAssignments();
               odb_SequenceConnectorOrientation connectorOrientations();
               odb_SequenceRigidBody rigidBodies();
               odb_SequencePretensionSection pretensionSections();
```

*instances*

[OdbInstance](pt02ch61pyo16.md) 对象的存储库。

*nodeSets*

[OdbSet](pt02ch61pyo24.md) 对象（指定节点集）的存储库。

*elementSets*

[OdbSet](pt02ch61pyo24.md) 对象（指定元素集）的存储库。

*surfaces*

[OdbSet](pt02ch61pyo24.md) 对象（指定表面）的存储库。

*nodes*

[OdbMeshNode](pt02ch61pyo19.md) 对象的序列。

*elements*

[OdbMeshElement](pt02ch61pyo18.md) 对象的序列。

*datumCsyses*

[OdbDatumCsys](pt02ch61pyo14.md) 对象的存储库。

*sectionAssignments*

[SectionAssignment](pt02ch62pyo01.md) 对象的序列。

*rigidBodies*

[OdbRigidBody](pt02ch61pyo22.md) 对象的序列。

*pretensionSections*

[OdbPretensionSection](pt02ch61pyo21.md) 对象的序列。

*connectorOrientations*

[ConnectorOrientation](pt02ch61pyo13.md#ker-odbassembly-connectororientation-cpp) 对象的序列。
