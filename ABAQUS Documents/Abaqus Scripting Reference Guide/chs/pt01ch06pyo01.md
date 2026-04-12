# 6.1 Assembly 对象





Assembly 对象是零件实例的容器。Assembly 对象没有构造函数命令。创建 [Model](pt01ch33pyo01.md) 对象时，Abaqus 创建 *rootAssembly* 成员。

**访问**

```
import assembly
mdb.models[*name*].rootAssembly
```

### 6.1.1 backup()

此方法对装配中的特征进行备份副本。`backup()` 方法与 `restore()` 方法结合使用。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.2 clearGeometryCache()

此方法删除几何缓存。删除几何缓存可减少正在使用的内存量。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.3 deleteAllFeatures()

此方法删除装配中的所有特征。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.4 deleteFeatures(...)

此方法从装配中删除指定的特征。

**必需参数**

*featureNames*

一个 String 序列，指定要从装配中删除的特征名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.1.5 excludeFromSimulation(...)

此方法将指定的零件实例从分析中排除。

**必需参数**

*instances*

一个 [PartInstance](pt01ch06pyo04.md) 对象序列，要从分析中排除。

*exclude*

一个 Bool，指定是否从分析中排除所选实例或将其包含。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.1.6 featurelistInfo()

此方法打印特征列表中所有特征的名称和状态。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.7 getMassProperties(...)

此方法返回装配、实例或区域的质量属性。仅支持梁、桁架、壳、实体、点、非结构质量和转动惯量元素。

**必需参数**

无。

**可选参数**

*regions*

一个 [PartInstance](pt01ch06pyo04.md) 对象序列或一个 [Region](pt01ch45pyo03.md) 对象序列，指定要查询其质量属性的零件实例或区域。默认情况下查询整个装配。

*relativeAccuracy*

一个 SymbolicConstant，指定几何计算的相对精度。可能的值为 LOW、MEDIUM 和 HIGH。默认值为 LOW。

*useMesh*

一个 Boolean，指定在计算中是否应在几何被网格划分时使用网格。默认值为 False。

*specifyDensity*

一个 Boolean，指定是否应在具有密度误差的区域（如未定义材料密度）中使用用户指定的密度。默认值为 False。

*density*

一个双精度值，指定要在具有密度误差的区域中使用的用户指定密度值。用户指定的密度应大于 0。

*specifyThickness*

一个 Boolean，指定是否应在具有厚度误差的区域（如未定义厚度）中使用用户指定的厚度。默认值为 False。

*thickness*

一个双精度值，指定要在具有厚度误差的区域中使用的用户指定厚度值。用户指定的厚度应大于 0。

*miAboutCenterOfMass*

一个 Boolean，指定是否应关于质心计算转动惯量。默认值为 True。

*miAboutPoint*

三个浮点数元组，指定要计算转动惯量的点坐标。默认情况下，如果转动惯量不是关于质心计算的，则它们将关于原点计算。

**返回值**

一个 Dictionary 对象，包含以下项目：

*area*：None 或一个 Float，指定指定面的面积总和。仅对壳的一个面计算面积。

*areaCentroid*：None 或三个 Float 元组，表示面积质心的坐标。

*volume*：None 或一个 Float，指定指定区域的体积。

*volumeCentroid*：None 或三个 Float 元组，表示体积质心的坐标。

*massFromMassPerUnitSurfaceArea*：None 或一个 Float，指定由单位表面积质量产生的质量。

*mass*：None 或一个 Float，指定指定区域的质量。它是总质量，包括来自单位表面积质量等量的质量。

*centerOfMass*：None 或三个 Float 元组，表示质心的坐标。

*momentOfInertia*：None 或六个 Float 元组，表示关于质心或指定点的转动惯量。

*warnings*：一个 SymbolicConstant 元组，表示计算质量属性时遇到的问题。可能的 SymbolicConstant 为：

UNSUPPORTED_ENTITIES：指定区域中存在一些不支持的实体。质量属性仅针对梁、桁架、壳、实体、点和非结构质量元素以及转动惯量元素计算。不会为轴对称元素、弹簧、连接器、垫圈或任何其他元素计算质量属性。

MISSING_THICKNESS：对于某些区域，截面定义缺少厚度值。

ZERO_THICKNESS：对于某些区域，截面定义的厚度值为零。

VARIABLE_THICKNESS：已忽略为某些区域指定的节点厚度或场厚度。

NON_APPLICABLE_THICKNESS：对于某些区域，厚度值不适用于在区域上指定的相应截面。

MISSING_DENSITY：对于某些区域，截面定义缺少材料密度值。

MISSING_MATERIAL_DEFINITION：对于某些区域，材料定义缺失。

ZERO_DENSITY：对于某些区域，截面定义的材料密度值为零。

UNSUPPORTED_DENSITY：对于某些区域，已指定负材料密度或温度相依密度，或者在复合截面中一个或多个层缺少材料值。

SHELL_OFFSETS：对于壳，此方法不考虑任何指定的偏移。

MISSING_SECTION_DEFINITION：对于某些区域，截面定义缺失。

UNSUPPORTED_SECTION_DEFINITION：某些区域提供的截面定义不受支持。

REINFORCEMENTS：此方法不考虑在模型上指定的任何增强。

SMEARED_PROPERTIES：对于具有复合截面分配的区域，密度被涂抹在整个厚度上。复合壳的体积质心和质心计算使用集总质量方法，其中体积和质量被假定为集中在壳的平面上。由于这些近似值，具有复合截面分配的区域的质量属性可能略有不准。

UNSUPPORTED_NON_STRUCTURAL_MASS_ENTITIES：此方法不考虑线上的任何非结构质量。

INCORRECT_MOMENT_OF_INERTIA：对于具有每体积非结构质量的几何区域，非结构质量被假定为位于区域质心处的点质量。因此，非结构质量的分布未被考虑，转动惯量可能不准确。使用网格来准确计算转动惯量。

MISSING_BEAM_ORIENTATIONS：对于具有梁截面分配的某些区域，梁截面方向缺失。

UNSUPPORTED_BEAM_PROFILES：此方法支持 Box、Pipe、Circular、Rectangular、Hexagonal、Trapezoidal、I、L、T、Arbitrary 和 Tapered 梁截面。任何其他梁截面不受支持。

TAPERED_BEAM_MI：锥形梁的转动惯量计算不准确。

SUBSTRUCTURE_INCORRECT_PROPERTIES：用户指定的密度和厚度不被考虑用于子结构。

**异常**

无。

### 6.1.8 getAngle(...)

此方法返回指定实体之间的角度。

**必需参数**

*plane1*

一个 [Face](pt01ch07pyo05.md)、[MeshFace](pt01ch31pyo08.md) 或一个 [Datum](pt01ch15pyo01.md) 对象，指定第一个平面。[Datum](pt01ch15pyo01.md) 对象必须表示基准平面。*plane1* 和 *line1* 参数是互斥的。必须指定其中之一。

*plane2*

一个 [Face](pt01ch07pyo05.md)、[MeshFace](pt01ch31pyo08.md) 或一个 [Datum](pt01ch15pyo01.md) 对象，指定第二个平面。[Datum](pt01ch15pyo01.md) 对象必须表示基准平面。*plane2* 和 *line2* 参数是互斥的。必须指定其中之一。

*line1*

一个 [Edge](pt01ch07pyo03.md)、[MeshEdge](pt01ch31pyo04.md) 或一个 [Datum](pt01ch15pyo01.md) 对象，指定第一条曲线。[Datum](pt01ch15pyo01.md) 对象必须表示基准轴。*plane1* 和 *line1* 参数是互斥的。必须指定其中之一。

*line2*

一个 [Edge](pt01ch07pyo03.md)、[MeshEdge](pt01ch31pyo04.md) 或一个 [Datum](pt01ch15pyo01.md) 对象，指定第二条曲线。[Datum](pt01ch15pyo01.md) 对象必须表示基准轴。*plane2* 和 *line2* 参数是互斥的。必须指定其中之一。

**可选参数**

*commonVertex*

如果两个选定的 [Edge](pt01ch07pyo03.md) 对象有多个公共顶点，则此 [Vertex](pt01ch07pyo15.md) 对象指定要评估角度的顶点。

**返回值**

一个 Float，指定指定实体之间的角度。如果您提供平面作为参数，Abaqus/CAE 使用平面的法线计算角度。

**异常**

无。

### 6.1.9 getCoordinates(...)

此方法返回指定点的坐标。

**必需参数**

*entity*

一个 [Vertex](pt01ch07pyo15.md)、[Datum](pt01ch15pyo01.md) 点、[MeshNode](pt01ch31pyo09.md) 或 [ReferencePoint](pt01ch07pyo13.md)，指定要查询的实体。

**可选参数**

无。

**返回值**

三个 Float 元组，表示指定点的坐标。

**异常**

无。

### 6.1.10 getDistance(...)

根据提供的参数，此方法返回以下之一：
- 两点之间的距离。
- 点与边缘之间的最小距离。
- 两个边缘之间的最小距离。

**必需参数**

*entity1*

一个 [Vertex](pt01ch07pyo15.md)、[Datum](pt01ch15pyo01.md) 点、[MeshNode](pt01ch31pyo09.md) 或 [Edge](pt01ch07pyo03.md)，指定要测量距离的第一个实体。

*entity2*

一个 [Vertex](pt01ch07pyo15.md)、[Datum](pt01ch15pyo01.md) 点、[MeshNode](pt01ch31pyo09.md) 或 [Edge](pt01ch07pyo03.md)，指定要测量距离的第二个实体。

**可选参数**

*printResults*

一个 Boolean，指定是否打印详细输出。默认值为 True。

**返回值**

一个 Float，指定计算的距离。

**异常**

无。

### 6.1.11 getFacesAndVerticesOfAttachmentLines(...)

给定一个边缘对象数组，此方法返回一个字典对象元组。每个对象包含五个成员，包括附着线和相关的面和顶点对象。

**必需参数**

*edges*

一个 [EdgeArray](pt01ch07pyo03.md) 对象，即 [Edge](pt01ch07pyo03.md) 对象的序列。

**可选参数**

无。

**返回值**

一个字典对象元组。每个字典包含五个项目，具有以下键：

*edge*：一个 [Edge](pt01ch07pyo03.md) 对象，指定附着线。

*startFace*：一个 [Face](pt01ch07pyo05.md) 对象，指定与附着线一端相关的面。

*endFace*：一个 [Face](pt01ch07pyo05.md) 对象，指定与附着线另一端相关的面。

*startVertex*：一个 [Vertex](pt01ch07pyo15.md) 对象，指定与附着线一端相关的顶点。此端也与 startFace 相关。

*endVertex*：一个 [Vertex](pt01ch07pyo15.md) 对象，指定与附着线另一端相关的顶点。此端也与 endFace 相关。

**异常**

无。

### 6.1.12 getSurfaceSections(...)

此方法返回分配给指定表面所包含区域的部分列表。

**必需参数**

*surface*

一个 String，指定表面名称。

**可选参数**

无。

**返回值**

一个 String 元组，表示部分名称。如果未找到部分名称，则该元组将包含一个空字符串。

**异常**

无。

### 6.1.13 importEafFile(...)

此方法将装配从 EAF 文件导入根装配。

**必需参数**

*filename*

一个 String，指定要从中导入装配的 EAF 文件的路径。

**可选参数**

仅当导入特定实例及其关联零件时，才使用以下可选参数。

*ids*

一个 Int 序列。每个 Int 是装配树中出现的唯一标识符或与 EAF 文件中零件关联的组件标识符。如果 *ids* 是一个空序列，则将导入所有出现或零件。默认值为空序列。

**返回值**

无

**异常**

无。

### 6.1.14 importParasolidFile(...)

此方法将装配从 Parasolid 文件导入根装配。

**必需参数**

*filename*

一个 String，指定要从中导入装配的 Parasolid 文件的路径。

**可选参数**

仅当导入特定实例及其关联零件时，才使用以下可选参数。

*ids*

一个 Int 序列。每个 Int 是装配树中出现的唯一标识符或与 EAF 文件中零件关联的组件标识符。如果 *ids* 是一个空序列，则将导入所有出现或零件。默认值为空序列。

**返回值**

无

**异常**

无。

### 6.1.15 importCatiaV4File(...)

此方法将装配从 CATIA V4 文件导入根装配。

**必需参数**

*filename*

一个 String，指定要从中导入装配的 CATIA V4 文件的路径。

**可选参数**

仅当导入特定实例及其关联零件时，才使用以下可选参数。

*ids*

一个 Int 序列。每个 Int 是装配树中出现的唯一标识符或与 EAF 文件中零件关联的组件标识符。如果 *ids* 是一个空序列，则将导入所有出现或零件。默认值为空序列。

**返回值**

无

**异常**

无。

### 6.1.16 importCatiaV5File(...)

此方法将装配从 CATIA V5 Elysium Neutral 文件导入根装配。

**必需参数**

*filename*

一个 String，指定要从中导入装配的 CATIA V5 Elysium Neutral 文件的路径。

**可选参数**

仅当导入特定实例及其关联零件时，才使用以下可选参数。

*ids*

一个 Int 序列。每个 Int 是装配树中出现的唯一标识符或与 EAF 文件中零件关联的组件标识符。如果 *ids* 是一个空序列，则将导入所有出现或零件。默认值为空序列。

**返回值**

无

**异常**

无。

### 6.1.17 importEnfFile(...)

此方法将从 Pro/ENGINEER、I-DEAS 或 CATIA V5 创建的 Elysium Neutral 文件中的装配导入根装配。

**必需参数**

*filename*

一个 String，指定要从中导入装配的 Elysium Neutral 文件的路径。

**可选参数**

仅当导入特定实例及其关联零件时，才使用以下可选参数。

*ids*

一个 Int 序列。每个 Int 是装配树中出现的唯一标识符或与 EAF 文件中零件关联的组件标识符。如果 *ids* 是一个空序列，则将导入所有出现或零件。默认值为空序列。

**返回值**

无

**异常**

无。

### 6.1.18 importIdeasFile(...)

此方法将装配从 I-DEAS Elysium Neutral 文件导入根装配。

**必需参数**

*filename*

一个 String，指定要从中导入装配的 I-DEAS Elysium Neutral 文件的路径。

**可选参数**

仅当导入特定实例及其关联零件时，才使用以下可选参数。

*ids*

一个 Int 序列。每个 Int 是装配树中出现的唯一标识符或与 EAF 文件中零件关联的组件标识符。如果 *ids* 是一个空序列，则将导入所有出现或零件。默认值为空序列。

**返回值**

无

**异常**

无。

### 6.1.19 importProEFile(...)

此方法将装配从 Pro/ENGINEER Elysium Neutral 文件导入根装配。

**必需参数**

*filename*

一个 String，指定要从中导入装配的 Pro/ENGINEER Elysium Neutral 文件的路径。

**可选参数**

仅当导入特定实例及其关联零件时，才使用以下可选参数。

*ids*

一个 Int 序列。每个 Int 是装配树中出现的唯一标识符或与 EAF 文件中零件关联的组件标识符。如果 *ids* 是一个空序列，则将导入所有出现或零件。默认值为空序列。

**返回值**

无

**异常**

无。

### 6.1.20 makeDependent(...)

此方法将指定的零件实例从独立转换为依赖零件实例。

**必需参数**

*instances*

一个 [PartInstance](pt01ch06pyo04.md) 对象序列，要转换为依赖零件实例。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.1.21 makeIndependent(...)

此方法将指定的零件实例从依赖转换为独立零件实例。

**必需参数**

*instances*

一个 [PartInstance](pt01ch06pyo04.md) 对象序列，要转换为独立零件实例。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.1.22 printAssignedSections()

此方法打印分配连接截面的摘要。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.23 printConnectorOrientations()

此方法打印连接器方向摘要。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.24 projectReferencesOntoSketch(...)

此方法将装配中的指定边缘、顶点和基准点投影到指定的 [ConstrainedSketch](pt01ch48pyo01.md) 对象上。边缘、顶点和基准点作为参考几何显示在草图上。

**必需参数**

*sketch*

要将边缘、顶点和基准点投影到的 [ConstrainedSketch](pt01ch48pyo01.md) 对象。

**可选参数**

*filter*

一个 SymbolicConstant，指定如何限制投影量。可能的值为 ALL_EDGES 和 COPLANAR_EDGES。如果 *filter*=COPLANAR_EDGES，则共面于草图表面的边缘是投影的唯一候选。默认值为 ALL_EDGES。

*upToFeature*

一个 Feature 对象，指定零件中基于特征的历程序列中的一个标记。Abaqus/CAE 仅将位于此标记指定的特征之前创建的零件实体投影到草图上。默认情况下，所有零件实体都是投影的候选。

*edges*

要投影到草图上的候选边缘序列。默认情况下，所有边缘都是投影的候选。

*vertices*

要投影到草图上的候选顶点序列。默认情况下，所有顶点都是投影的候选。

**返回值**

无

**异常**

无。

### 6.1.25 queryCachedStates()

此方法显示装配缓存中几何状态相对于特征序列的位置。输出显示在消息区域。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.26 regenerate()

此方法重新生成装配并使其与装配参数的最新值保持同步。当您修改装配的特征时，延迟重新生成可能很方便，因为重新生成可能耗时。相反，当您修改包含在装配中的零件的特征时，应使用此命令重新生成装配。当您重新生成装配时，它将反映您对零件所做的更改。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.27 regenerationWarnings()

此方法打印与特征关联的任何重新生成警告。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.28 restore()

此方法将装配中所有特征的参数恢复到失败重新生成之前的值。在失败重新生成后使用 `restore` 方法，然后是 `regenerate` 命令。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.29 resumeAllFeatures()

此方法恢复零件或装配中被抑制的所有特征。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.30 resumeFeatures(...)

此方法恢复装配中被抑制的指定特征。

**必需参数**

*featureNames*

一个 String 序列，指定要恢复的特征名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.1.31 resumeLastSetFeatures()

此方法恢复装配中最后被抑制的一组特征。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.32 rotate(...)

此方法将给定实例旋转指定量。

**必需参数**

*instanceList*

一个 String 序列，指定要旋转的实例名称。

*axisPoint*

三个 Float 序列，指定轴上一点的坐标。

*axisDirection*

三个 Float 序列，指定轴的方向。

*angle*

一个 Float，指定旋转角度（以度为单位）。使用右手定则确定方向。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.1.33 translate(...)

此方法将给定实例平移指定量。

**必需参数**

*instanceList*

一个 String 序列，指定要平移的实例名称。

*vector*

三个 Float 序列，指定平移向量。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.1.34 saveGeometryCache()

此方法缓存当前几何，这可以提高重新生成性能。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.35 setValues(...)

此方法修改与指定装配关联的行为。

**必需参数**

*regenerateConstraintsTogether*

一个 Boolean，指定在重新生成其他装配特征之前，是否应一起重新生成装配中的定位约束。默认值为 ON。

如果装配具有位置约束特征且您修改了 *regenerateConstraintsTogether* 的值，Abaqus/CAE 将重新生成装配特征。

**可选参数**

无。

**返回值**

无

**异常**

如果装配中的一个或多个特征重新生成失败：

```
FeatureError: Regeneration failed
```

### 6.1.36 suppressFeatures(...)

此方法抑制指定的特征。

**必需参数**

*featureNames*

一个 String 序列，指定要在装配中抑制的特征名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.1.37 unlinkInstances(...)

此方法将指定的 [PartInstance](pt01ch06pyo04.md) 对象从链接子实例转换为常规实例。所选实例关联的零件也将转换为常规零件。

**必需参数**

*instances*

一个 [PartInstance](pt01ch06pyo04.md) 对象序列，要转换为常规零件实例。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.1.38 writeAcisFile(...)

此方法将装配导出为 ACIS 格式的命名文件。

**必需参数**

*fileName*

一个 String，指定要写入的文件名。

**可选参数**

*version*

一个 Float，指定 ACIS 版本。例如，Float "12.0" 对应于 ACIS Version 12.0。默认值为当前版本的 ACIS。

**返回值**

无

**异常**

无。

### 6.1.39 writeCADParameters(...)

此方法将参数写入从 CAD 系统导入的参数文件。

**必需参数**

*paramFile*

一个 String，指定参数文件名。

**可选参数**

*modifiedParams*

一个元组元组，每个元组包含零件名称、参数名称和修改后的参数值。默认值为空元组。

*updatePaths*

一个 Bool，指定如果 CAD 模型文件存在于当前目录中，是否更新 *parameterFile* 中指定的 CAD 模型文件的路径。

**返回值**

无

**异常**

无。

### 6.1.40 lock()

此方法锁定装配。锁定装配可防止任何进一步的更改触发装配的重新生成。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.41 unlock()

此方法解锁装配。解锁装配允许在对其任何修改后重新生成。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.1.42 setMeshNumberingControl(...)

此方法在 Abaqus/CAE 生成网格之前或之后更改指定独立零件实例的起始节点和/或元素标签。对于网格化的实例，Abaqus/CAE 在保留原始顺序和增量的情况下更改节点和/或元素标签。

**必需参数**

*instances*

一个 [PartInstance](pt01ch06pyo04.md) 对象序列，要更改起始节点和/或元素标签。

**可选参数**

*startNodeLabel*

一个正 Integer，指定新的起始节点标签。

*startElemLabel*

一个正 Integer，指定新的起始元素标签。

**返回值**

无

**异常**

无。

### 6.1.43 copyMeshPattern(...)

此方法从由一组壳元素或元素面组成源区域复制网格图案到目标面，在源和目标之间以一对一对应方式映射节点和元素。

**必需参数**

无。

**可选参数**

*elements*

一个 [MeshElement](pt01ch31pyo05.md) 对象序列或包含元素的 Set 对象，指定源区域。

*faces*

一组 [Face](pt01ch07pyo05.md) 对象，这些面具有关联的壳元素或元素面，指定源区域。

*elemFaces*

一组 [MeshFace](pt01ch31pyo08.md) 对象，指定源区域。

*targetFace*

一个 [MeshFace](pt01ch31pyo08.md) 对象，指定目标区域。目标面可以来自不同的零件实例。

*nodes*

一组 MeshNode 对象或包含节点的 Set 对象，位于源区域的边界上，这些节点将被定位到目标面的边界。

*coordinates*

三维坐标元组序列，指定每个给定节点的坐标。当指定时，坐标元组的数量必须与给定节点的数量匹配，并按照与给定节点 *升序* 相对应的顺序排列。这些坐标是将成为对应于所提供节点的目标面上节点的网格节点位置。

**返回值**

无

**异常**

无。

### 6.1.44 smoothNodes(...)

此方法平滑给定本地网格的节点，将它们局部移动到更优化的位置，从而提高网格质量。

**必需参数**

无。

**可选参数**

*nodes*

一组 MeshNode 对象或包含节点的 Set 对象。将平滑不是本地网格一部分的节点。

*coordinates*

一组 MeshNode 对象或包含节点的 Set 对象。

**返回值**

无

**异常**

无。

### 6.1.45 成员

Assembly 对象可以具有以下成员：

*isOutOfDate*

一个 Int，指定特征参数已被修改但装配尚未重新生成。可能的值为 0 和 1。

*timeStamp*

一个 Float，指定装配上次修改时的时间指示。

*isLocked*

一个 Int，指定装配是否被锁定。可能的值为 0 和 1。

*regenerateConstraintsTogether*

一个 Boolean，指定在重新生成其他装配特征之前，是否应一起重新生成装配中的定位约束。默认值为 ON。

如果装配具有位置约束特征且您修改了 *regenerateConstraintsTogether* 的值，Abaqus/CAE 将重新生成装配特征。

*vertices*

一个 [VertexArray](pt01ch07pyo15.md) 对象，指定存在于装配级别的所有顶点。此成员不提供对实例级别顶点的访问。

*edges*

一个 [EdgeArray](pt01ch07pyo03.md) 对象，指定存在于装配级别的所有边缘。此成员不提供对实例级别边缘的访问。

*elements*

一个 [MeshElementArray](pt01ch31pyo05.md) 对象，指定存在于装配级别的所有元素。此成员不提供对实例级别元素的访问。

*nodes*

一个 [MeshNodeArray](pt01ch31pyo09.md) 对象，指定存在于装配级别的所有节点。此成员不提供对实例级别节点的访问。

*instances*

一个 [PartInstance](pt01ch06pyo04.md) 对象仓库。

*datums*

一个 [Datum](pt01ch15pyo01.md) 对象仓库，指定装配中的所有 [Datum](pt01ch15pyo01.md) 对象。

*features*

一个 [Feature](pt01ch20pyo01.md) 对象仓库，指定装配中的所有 [Feature](pt01ch20pyo01.md) 对象。

*featuresById*

一个 [Feature](pt01ch20pyo01.md) 对象仓库，指定装配中的所有 [Feature](pt01ch20pyo01.md) 对象。

`featuresById` 仓库中的 [Feature](pt01ch20pyo01.md) 对象与 `features` 仓库中的 [Feature](pt01ch20pyo01.md) 对象相同。但是，`featuresById` 仓库中对象的键是一个整数，指定 *ID*，而 `features` 仓库中对象的键是一个字符串，指定 *name*。

*surfaces*

一个 [Surface](pt01ch45pyo05.md) 对象仓库。更多信息，请参见[第 45 章，"区域命令"](pt01ch45.md)。

*allSurfaces*

一个 [Surface](pt01ch45pyo05.md) 对象仓库。更多信息，请参见[第 45 章，"区域命令"](pt01ch45.md)。

*allInternalSurfaces*

一个 [Surface](pt01ch45pyo05.md) 对象仓库，指定拾取的区域。

*sets*

一个 [Set](pt01ch45pyo04.md) 对象仓库。

*allSets*

一个 [Set](pt01ch45pyo04.md) 对象仓库。更多信息，请参见[第 45 章，"区域命令"](pt01ch45.md)。

*allInternalSets*

一个 [Set](pt01ch45pyo04.md) 对象仓库，指定拾取的区域。

*skins*

一个 [Skin](pt01ch45pyo06.md) 对象仓库，指定在装配上创建的蒙皮。

*stringers*

一个 [Stringer](pt01ch45pyo07.md) 对象仓库，指定在装配上创建的纵梁。

*referencePoints*

一个 [ReferencePoint](pt01ch07pyo13.md) 对象仓库。

*modelInstances*

一个 [ModelInstance](pt01ch06pyo05.md) 对象仓库。

*allinstances*

一个 [PartInstance](pt01ch06pyo04.md) 对象，指定 PartInstances，和一个 [ModelInstance](pt01ch06pyo05.md) 对象，指定 ModelInstances。

*engineeringFeatures*

一个 [EngineeringFeature](pt01ch19pyo01.md) 对象。

*modelName*

一个 String，指定装配所属模型的名称。

*connectorOrientations*

一个 [ConnectorOrientationArray](pt01ch06pyo02.md) 对象。

*sectionAssignments*

一个 [SectionAssignmentArray](pt01ch44pyo01.md) 对象。




