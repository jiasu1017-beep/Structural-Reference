# 40.1 BasicOptions 对象

BasicOptions 对象存储与 [OdbDisplay](pt01ch35pyo01.md) 对象关联的值和属性。BasicOptions 对象没有构造函数命令。导入 Visualization 模块时，Abaqus 会创建 *defaultOdbDisplay.basicOptions* 成员。当 Abaqus 创建 [OdbDisplay](pt01ch35pyo01.md) 对象时，会使用 *defaultOdbDisplay.basicOptions* 的值创建 *basicOptions* 成员。创建视口时，Abaqus 会使用先前活动视口的属性创建 *odbDisplay* 成员。先前活动视口包含该会话的 *defaultOdbDisplay* 对象的属性。这些属性从先前活动视口复制到新视口。

BasicOptions 对象通过以下两种方式之一访问：
- 默认基本选项。创建其他 *basicOptions* 成员时使用这些设置作为默认值。可以设置这些设置来自定义用户首选项。
- 与特定视口关联的基本选项。

**访问**

```
import visualization
session.defaultOdbDisplay.basicOptions
session.viewports[*name*].layers[*name*].odbDisplay.basicOptions
session.viewports[*name*].odbDisplay.basicOptions
```

### 40.1.1 setValues(...)

此方法修改 BasicOptions 对象。

**必需参数**

无。

**可选参数**

*options*

 BasicOptions 对象，指定要复制的值。如果还有其他参数提供给 `setValues`，它们将覆盖 *options* 中的值。默认值为 `None`。

*cameraCsysName*

 String，指定驱动移动摄像头的坐标系名称。

*cameraMovesWithCsys*

 Boolean，指定摄像头是否随坐标系移动。默认值为 OFF。

*cameraFollowsRotation*

 Boolean，指定摄像头移动时是否跟随坐标系的旋转。默认值为 OFF。

*averagingThreshold*

 Float，指定节点平均阈值百分比。可能的值为 0 ![](../graphics/ker_eqn00048.gif) *averagingThreshold* ![](../graphics/ker_eqn00048.gif) 100。默认值为 75.0。

*quantityToPlot*

 SymbolicConstant，指定要绘制的数据。可选值为 FIELD_OUTPUT 和 DISCONTINUITIES。默认值为 FIELD_OUTPUT。

*curveRefinementLevel*

 SymbolicConstant，指定绘制曲线的细化级别。可选值为 EXTRA_COARSE、COARSE、MEDIUM、FINE 和 EXTRA_FINE。默认值为 COARSE。

*noResultsColor*

 String，指定没有结果的单元的颜色。默认值为 "White"。

*featureAngle*

 Float，指定当 *visibleEdges*=FEATURE 时使用的特征角度。默认值为 30.0。

*otherSymbolSize*

 Int，指定各种符号（边界条件、耦合约束等）的大小。默认值为 6。

*renderBeamProfiles*

 Boolean，指定是否渲染梁轮廓。默认值为 OFF。

*beamScaleFactor*

 Float，指定梁轮廓比例因子。beamScaleFactor 必须大于零。默认值为 1.0。

*renderShellThickness*

 Boolean，指定是否渲染壳厚度。默认值为 OFF。

*shellScaleFactor*

 Float，指定壳厚度比例因子。shellScaleFactor 必须大于零。默认值为 1.0。

*accountForDeactivatedElems*

 Boolean，指定是否考虑已停用的单元。默认值为 ON。

*bcDisplay*

 Boolean，指定是否显示边界条件。默认值为 OFF。

*connectorDisplay*

 Boolean，指定是否显示连接器。默认值为 OFF。

*highlightConnectorPts*

 Boolean，指定是否高亮显示连接器点。默认值为 ON。

*showConnectorAxes*

 Boolean，指定是否显示连接器取向或坐标系。默认值为 ON。

*showConnectorType*

 Boolean，指定是否显示描述连接器类型的文本。默认值为 ON。

*pointElements*

 Boolean，指定是否显示点类型单元。默认值为 ON。

*referencePoints*

 Boolean，指定是否显示参考点。*referencePoints* 仅在 *pointElements*=ON 时有效。默认值为 ON。

*massElements*

 Boolean，指定是否显示质量、热容和惯性单元。*massElements* 仅在 *pointElements*=ON 时有效。默认值为 OFF。

*springElements*

 Boolean，指定是否显示弹簧和阻尼器单元。*springElements* 仅在 *pointElements*=ON 时有效。默认值为 OFF。

*spotWelds*

 Boolean，指定是否显示点焊和分布式耦合单元。*spotWelds* 仅在 *pointElements*=ON 时有效。默认值为 OFF。

*tracerParticles*

 Boolean，指定是否显示示踪粒子。*tracerParticles* 仅在 *pointElements*=ON 时有效。默认值为 OFF。

*pc3dElements*

 Boolean，指定是否显示 PC3D 单元。*pc3dElements* 仅在 *pointElements*=ON 时有效。默认值为 ON。

*pd3dElements*

 Boolean，指定是否显示 PD3D 单元。*pd3dElements* 仅在 *pointElements*=ON 时有效。默认值为 ON。

*sweepArs*

 Boolean，指定是否扫描解析曲面。默认值为 ON 或 OFF，取决于模型的特征。

*sweepElem*

 Boolean，指定是否扫描可变形单元。默认值为 ON 或 OFF，取决于模型的特征。

*sweepStartAngleArs*

 Float，指定当 *sweepArs*=ON 时开始扫描解析曲面的起始角度（度）。默认值为 0.0。

*sweepStartAngleElem*

 Float，指定当 *sweepElem*=ON 时开始扫描模型的起始角度（度）。默认值为 0.0。

*sweepEndAngleArs*

 Float，指定当 *sweepArs*=ON 时扫描解析曲面的结束角度（度）。默认值为 360.0。

*sweepEndAngleElem*

 Float，指定当 *sweepElem*=ON 时扫描模型的结束角度（度）。默认值为 180.0。

*numSweepSegmentsArs*

 Int，指定当 *sweepArs*=ON 时显示的分段数。默认值为 10 或 20，取决于模型的特征。

*numSweepSegmentsElem*

 Int，指定当 *sweepElem*=ON 时显示的分段数。默认值为 10 或 20，取决于模型的特征。

*numericForm*

 SymbolicConstant，指定显示包含复数的结果时使用的数字形式。可选值为 COMPLEX_MAGNITUDE、COMPLEX_PHASE、REAL、IMAGINARY 和 COMPLEX_MAG_AT_ANGLE。默认值为 REAL。

*complexAngle*

 Float，指定当 *numericForm*=COMPLEX_MAG_AT_ANGLE 时显示包含复数的结果的角度（度）。默认值为 0.0。

*sectionResults*

 SymbolicConstant，指定要使用的截面点。可选值为 USE_BOTTOM、USE_TOP、USE_BOTTOM_AND_TOP 和 USE_ENVELOPE。默认值为 USE_BOTTOM。

*envelopeCriteria*

 SymbolicConstant，指定包络准则。可选值为 MAX_VALUE、MIN_VALUE 和 MAX_ABS_VALUE。默认值为 MAX_ABS_VALUE。

*envelopeDataPosition*

 SymbolicConstant，指定包络计算的输出位置。可选值为 CENTROID、ELEMENT_NODAL 和 INTEGRATION_POINT。默认值为 INTEGRATION_POINT。

*plyResultLocation*

 SymbolicConstant，指定层合板结果位置。可选值为 BOTTOM、MIDDLE、TOP 和 TOP_AND_BOTTOM。默认值为 MIDDLE。

*sectionPointScheme*

 SymbolicConstant，指定截面点方案。可选值为 CATEGORY_BASED 和 PLY_BASED。默认值为 CATEGORY_BASED。

*sweepSectors*

 Boolean，指定是否扫描循环对称扇区。默认值为 OFF。

*sectorSelectionType*

 SymbolicConstant，指定如何选择扇区进行扫描。可选值为 SELECT_BY_NUMBER、SELECT_BY_ANGLE 和 SELECT_ALL。默认值为 SELECT_BY_NUMBER。

*selectedSectorNumbers*

 Int 序列，指定当 *sectorSelectionType*=SELECT_BY_NUMBER 时要显示的扇区。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *selectedSectorNumbers* ![](../graphics/ker_eqn00013.gif) 扇区数。默认值为 (1)。

*sweepSectorStartAngle*

 Float，指定当 *sweepSectors*=ON 时开始扫描循环对称扇区的角度（度）。可能的值为扇区角度的倍数，使得 0 ![](../graphics/ker_eqn00013.gif) *sweepSectorStartAngle* ![](../graphics/ker_eqn00013.gif) 360。默认值为 0.0。

*sweepSectorEndAngle*

 Float，指定当 *sweepSectors*=ON 时扫描循环对称扇区的结束角度（度）。可能的值为扇区角度的倍数，使得 0 ![](../graphics/ker_eqn00048.gif) *sweepSectorEndAngle* ![](../graphics/ker_eqn00013.gif) 360。默认值为 360.0。

*extrudeArs*

 Boolean，指定是否拉伸解析曲面。默认值为 ON 或 OFF，取决于模型的特征。

*extrudeArsDepthAutoCompute*

 Boolean，指定拉伸解析曲面时是否使用自动深度确定。默认值为 ON。

*extrudeElem*

 Boolean，指定是否拉伸可变形单元。默认值为 ON 或 OFF，取决于模型的特征。

*extrudeArsDepth*

 Float，指定当 *extrudeArs*=ON 时拉伸解析曲面的深度（模型单位）。默认值为 1.0。

*extrudeElemDepth*

 Float，指定当 *extrudeElem*=ON 时拉伸可变形单元的深度（模型单位）。默认值为 1.0。

*mirrorPatternOrder*

 SymbolicConstant，指定创建镜像图案的操作顺序。可选值为 MIRROR_RECT_CIRC、RECT_MIRROR_CIRC、MIRROR_CIRC_RECT、RECT_CIRC_MIRROR、CIRC_MIRROR_RECT 和 CIRC_RECT_MIRROR。默认值为 MIRROR_RECT_CIRC。

*mirrorCsysName*

 SymbolicConstant GLOBAL 或 String，指定镜像坐标系的名称。默认值为 GLOBAL。

*mirrorAboutXyPlane*

 Boolean，指定是否关于 XY 平面镜像。默认值为 OFF。

*mirrorAboutXzPlane*

 Boolean，指定是否关于 XZ 平面镜像。默认值为 OFF。

*mirrorAboutYzPlane*

 Boolean，指定是否关于 YZ 平面镜像。默认值为 OFF。

*mirrorDisplayBodies*

 Boolean，指定是否镜像显示体。默认值为 OFF。

*patternCsysName*

 SymbolicConstant GLOBAL 或 String，指定图案坐标系的名称。默认值为 GLOBAL。

*patternNumX*

 Int，指定矩形图案在 X 方向上创建的图案数。默认值为 1。

*patternNumY*

 Int，指定矩形图案在 Y 方向上创建的图案数。默认值为 1。

*patternNumZ*

 Int，指定矩形图案在 Z 方向上创建的图案数。默认值为 1。

*patternOffsetX*

 Float，指定矩形图案沿 X 轴的偏移量。默认值为 0.0。

*patternOffsetY*

 Float，指定矩形图案沿 Y 轴的偏移量。默认值为 0.0。

*patternOffsetZ*

 Float，指定矩形图案沿 Z 轴的偏移量。默认值为 0.0。

*patternRotationAxis*

 SymbolicConstant，指定圆形图案的旋转轴。可选值为 XAXIS、YAXIS 和 ZAXIS。默认值为 ZAXIS。

*patternTotalAngle*

 Float，指定圆形图案的总角度。默认值为 360.0。

*patternNumCircular*

 Int，指定圆形图案中创建的图案数。默认值为 1。

*couplingDisplay*

 Boolean，指定是否显示耦合约束。默认值为 ON。

*coordSystemDisplay*

 Boolean，指定是否显示坐标系。默认值为 OFF。

*scratchCoordSystemDisplay*

 Boolean，指定是否显示代表用户定义取向的坐标系。默认值为 OFF。

*transformationType*

 SymbolicConstant，指定要应用于 PrimaryVariable 的变换。可选值为 DEFAULT、NODAL、USER_SPECIFIED、ANGULAR 和 LAYUP_ORIENTATION。默认值为 DEFAULT。

如果 *transformationType*=NODAL，Abaqus 将使用分析中定义的任何取向（通过 [*TRANSFORM*](../key/key-link.md#usb-kws-mtransform) 选项）变换节点向量场。设置 *transformationType*=NODAL 对基于单元的结果没有影响。

如果 *transformationType*=USER_SPECIFIED，Abaqus 将把张量和向量场变换到由 *datumCsys* 指定的坐标系中。

如果 *transformationType*=LAYUP_ORIENTATION，Abaqus 将把张量和向量场变换到复合截面中定义的层合板取向。odb 需要包含字段 SORIENT 才能使用此选项。

*datumCsys*

 [DatumCsys](pt01ch15pyo03.md) 对象，指定当 *transformationType*=USER_SPECIFIED 时用于结果变换的坐标系。

*rigidTransformPrimary*

 Boolean，指定是否基于活动的用户特定系统对节点向量数据集执行刚性变换。默认值为 OFF。

*rigidTransformDeformed*

 Boolean，指定是否基于活动的用户特定系统对当前变形变量执行刚性变换。默认值为 OFF。

*transformOnDeformed*

 Boolean，指定是否在变换计算中考虑变形的影响。默认值为 ON。

*averageElementOutput*

 Boolean，指定是否平均单元输出。默认值为 ON。

*averageOnlyDisplayed*

 Boolean，指定是否仅对显示的单元进行平均。默认值为 ON。

*computeOutput*

 SymbolicConstant，指定要执行的计算顺序。可选值为 EXTRAPOLATE_AVERAGE_COMPUTE、EXTRAPOLATE_COMPUTE_AVERAGE、EXTRAPOLATE_COMPUTE、EXTRAPOLATE_COMPUTE_DISCONTINUITIES 和 RAW_DATA。默认值为 EXTRAPOLATE_AVERAGE_COMPUTE。

*regionBoundaries*

 SymbolicConstant，指定平均区域边界的类型。可选值为 NONE、ODB_REGIONS、ELEMENT_SET 和 DISPLAY_GROUPS。默认值为 ODB_REGIONS。

*useRegionBoundaries*

 Boolean，指定平均时是否使用区域边界。默认值为 ON。

*userRegions*

字符串序列，指定定义平均区域边界的单元集或显示组名称（取决于 `regionBoundaries` 的值）。默认值为空序列。

*includeFeatureBoundaries*

 Boolean，指定是否基于特征边缘为壳和膜包含额外的平均边界。默认值为 ON。

**返回值**

无

**异常**

如果 *featureAngle* 不在有效范围内：

```
RangeError: featureAngle must be a float in the range 0-90, inclusive
```

### 40.1.2 成员

BasicOptions 对象可以具有以下成员：

*regionAveraging*

 Boolean，指定计算值时是否忽略区域边界。默认值为 ON。

*cameraMovesWithCsys*

 Boolean，指定摄像头是否随坐标系移动。默认值为 OFF。

*cameraFollowsRotation*

 Boolean，指定摄像头移动时是否跟随坐标系的旋转。默认值为 OFF。

*averagingThreshold*

 Float，指定节点平均阈值百分比。可能的值为 0 ![](../graphics/ker_eqn00048.gif) *averagingThreshold* ![](../graphics/ker_eqn00048.gif) 100。默认值为 75.0。

*quantityToPlot*

 SymbolicConstant，指定要绘制的数据。可选值为 FIELD_OUTPUT 和 DISCONTINUITIES。默认值为 FIELD_OUTPUT。

*extrapAlgorithm*

 SymbolicConstant，指定外推算法。此成员仅供内部使用。唯一可能的值为 EXTRAP_COMPUTE_AVERAGE。

*curveRefinementLevel*

 SymbolicConstant，指定绘制曲线的细化级别。可选值为 EXTRA_COARSE、COARSE、MEDIUM、FINE 和 EXTRA_FINE。默认值为 COARSE。

*featureAngle*

 Float，指定当 *visibleEdges*=FEATURE 时使用的特征角度。默认值为 30.0。

*otherSymbolSize*

 Int，指定各种符号（边界条件、耦合约束等）的大小。默认值为 6。

*renderBeamProfiles*

 Boolean，指定是否渲染梁轮廓。默认值为 OFF。

*beamScaleFactor*

 Float，指定梁轮廓比例因子。beamScaleFactor 必须大于零。默认值为 1.0。

*renderShellThickness*

 Boolean，指定是否渲染壳厚度。默认值为 OFF。

*shellScaleFactor*

 Float，指定壳厚度比例因子。shellScaleFactor 必须大于零。默认值为 1.0。

*accountForDeactivatedElems*

 Boolean，指定是否考虑已停用的单元。默认值为 ON。

*bcDisplay*

 Boolean，指定是否显示边界条件。默认值为 OFF。

*connectorDisplay*

 Boolean，指定是否显示连接器。默认值为 OFF。

*highlightConnectorPts*

 Boolean，指定是否高亮显示连接器点。默认值为 ON。

*showConnectorAxes*

 Boolean，指定是否显示连接器取向或坐标系。默认值为 ON。

*showConnectorType*

 Boolean，指定是否显示描述连接器类型的文本。默认值为 ON。

*pointElements*

 Boolean，指定是否显示点类型单元。默认值为 ON。

*referencePoints*

 Boolean，指定是否显示参考点。*referencePoints* 仅在 *pointElements*=ON 时有效。默认值为 ON。

*massElements*

 Boolean，指定是否显示质量、热容和惯性单元。*massElements* 仅在 *pointElements*=ON 时有效。默认值为 OFF。

*springElements*

 Boolean，指定是否显示弹簧和阻尼器单元。*springElements* 仅在 *pointElements*=ON 时有效。默认值为 OFF。

*spotWelds*

 Boolean，指定是否显示点焊和分布式耦合单元。*spotWelds* 仅在 *pointElements*=ON 时有效。默认值为 OFF。

*tracerParticles*

 Boolean，指定是否显示示踪粒子。*tracerParticles* 仅在 *pointElements*=ON 时有效。默认值为 OFF。

*pc3dElements*

 Boolean，指定是否显示 PC3D 单元。*pc3dElements* 仅在 *pointElements*=ON 时有效。默认值为 ON。

*pd3dElements*

 Boolean，指定是否显示 PD3D 单元。*pd3dElements* 仅在 *pointElements*=ON 时有效。默认值为 ON。

*sweepArs*

 Boolean，指定是否扫描解析曲面。默认值为 ON 或 OFF，取决于模型的特征。

*sweepElem*

 Boolean，指定是否扫描可变形单元。默认值为 ON 或 OFF，取决于模型的特征。

*sweepStartAngleArs*

 Float，指定当 *sweepArs*=ON 时开始扫描解析曲面的起始角度（度）。默认值为 0.0。

*sweepStartAngleElem*

 Float，指定当 *sweepElem*=ON 时开始扫描模型的起始角度（度）。默认值为 0.0。

*sweepEndAngleArs*

 Float，指定当 *sweepArs*=ON 时扫描解析曲面的结束角度（度）。默认值为 360.0。

*sweepEndAngleElem*

 Float，指定当 *sweepElem*=ON 时扫描模型的结束角度（度）。默认值为 180.0。

*numSweepSegmentsArs*

 Int，指定当 *sweepArs*=ON 时显示的分段数。默认值为 10 或 20，取决于模型的特征。

*numSweepSegmentsElem*

 Int，指定当 *sweepElem*=ON 时显示的分段数。默认值为 10 或 20，取决于模型的特征。

*numericForm*

 SymbolicConstant，指定显示包含复数的结果时使用的数字形式。可选值为 COMPLEX_MAGNITUDE、COMPLEX_PHASE、REAL、IMAGINARY 和 COMPLEX_MAG_AT_ANGLE。默认值为 REAL。

*complexAngle*

 Float，指定当 *numericForm*=COMPLEX_MAG_AT_ANGLE 时显示包含复数的结果的角度（度）。默认值为 0.0。

*sectionResults*

 SymbolicConstant，指定要使用的截面点。可选值为 USE_BOTTOM、USE_TOP、USE_BOTTOM_AND_TOP 和 USE_ENVELOPE。默认值为 USE_BOTTOM。

*envelopeCriteria*

 SymbolicConstant，指定包络准则。可选值为 MAX_VALUE、MIN_VALUE 和 MAX_ABS_VALUE。默认值为 MAX_ABS_VALUE。

*envelopeDataPosition*

 SymbolicConstant，指定包络计算的输出位置。可选值为 CENTROID、ELEMENT_NODAL 和 INTEGRATION_POINT。默认值为 INTEGRATION_POINT。

*plyResultLocation*

 SymbolicConstant，指定层合板结果位置。可选值为 BOTTOM、MIDDLE、TOP 和 TOP_AND_BOTTOM。默认值为 MIDDLE。

*sectionPointScheme*

 SymbolicConstant，指定截面点方案。可选值为 CATEGORY_BASED 和 PLY_BASED。默认值为 CATEGORY_BASED。

*sweepSectors*

 Boolean，指定是否扫描循环对称扇区。默认值为 OFF。

*sectorSelectionType*

 SymbolicConstant，指定如何选择扇区进行扫描。可选值为 SELECT_BY_NUMBER、SELECT_BY_ANGLE 和 SELECT_ALL。默认值为 SELECT_BY_NUMBER。

*sweepSectorStartAngle*

 Float，指定当 *sweepSectors*=ON 时开始扫描循环对称扇区的角度（度）。可能的值为扇区角度的倍数，使得 0 ![](../graphics/ker_eqn00013.gif) *sweepSectorStartAngle* ![](../graphics/ker_eqn00013.gif) 360。默认值为 0.0。

*sweepSectorEndAngle*

 Float，指定当 *sweepSectors*=ON 时扫描循环对称扇区的结束角度（度）。可能的值为扇区角度的倍数，使得 0 ![](../graphics/ker_eqn00048.gif) *sweepSectorEndAngle* ![](../graphics/ker_eqn00013.gif) 360。默认值为 360.0。

*extrudeArs*

 Boolean，指定是否拉伸解析曲面。默认值为 ON 或 OFF，取决于模型的特征。

*extrudeArsDepthAutoCompute*

 Boolean，指定拉伸解析曲面时是否使用自动深度确定。默认值为 ON。

*extrudeElem*

 Boolean，指定是否拉伸可变形单元。默认值为 ON 或 OFF，取决于模型的特征。

*extrudeArsDepth*

 Float，指定当 *extrudeArs*=ON 时拉伸解析曲面的深度（模型单位）。默认值为 1.0。

*extrudeElemDepth*

 Float，指定当 *extrudeElem*=ON 时拉伸可变形单元的深度（模型单位）。默认值为 1.0。

*mirrorPatternOrder*

 SymbolicConstant，指定创建镜像图案的操作顺序。可选值为 MIRROR_RECT_CIRC、RECT_MIRROR_CIRC、MIRROR_CIRC_RECT、RECT_CIRC_MIRROR、CIRC_MIRROR_RECT 和 CIRC_RECT_MIRROR。默认值为 MIRROR_RECT_CIRC。

*mirrorAboutXyPlane*

 Boolean，指定是否关于 XY 平面镜像。默认值为 OFF。

*mirrorAboutXzPlane*

 Boolean，指定是否关于 XZ 平面镜像。默认值为 OFF。

*mirrorAboutYzPlane*

 Boolean，指定是否关于 YZ 平面镜像。默认值为 OFF。

*mirrorDisplayBodies*

 Boolean，指定是否镜像显示体。默认值为 OFF。

*patternNumX*

 Int，指定矩形图案在 X 方向上创建的图案数。默认值为 1。

*patternNumY*

 Int，指定矩形图案在 Y 方向上创建的图案数。默认值为 1。

*patternNumZ*

 Int，指定矩形图案在 Z 方向上创建的图案数。默认值为 1。

*patternOffsetX*

 Float，指定矩形图案沿 X 轴的偏移量。默认值为 0.0。

*patternOffsetY*

 Float，指定矩形图案沿 Y 轴的偏移量。默认值为 0.0。

*patternOffsetZ*

 Float，指定矩形图案沿 Z 轴的偏移量。默认值为 0.0。

*patternRotationAxis*

 SymbolicConstant，指定圆形图案的旋转轴。可选值为 XAXIS、YAXIS 和 ZAXIS。默认值为 ZAXIS。

*patternTotalAngle*

 Float，指定圆形图案的总角度。默认值为 360.0。

*patternNumCircular*

 Int，指定圆形图案中创建的图案数。默认值为 1。

*couplingDisplay*

 Boolean，指定是否显示耦合约束。默认值为 ON。

*coordSystemDisplay*

 Boolean，指定是否显示坐标系。默认值为 OFF。

*scratchCoordSystemDisplay*

 Boolean，指定是否显示代表用户定义取向的坐标系。默认值为 OFF。

*transformationType*

 SymbolicConstant，指定要应用于 PrimaryVariable 的变换。可选值为 DEFAULT、NODAL、USER_SPECIFIED、ANGULAR 和 LAYUP_ORIENTATION。默认值为 DEFAULT。

如果 *transformationType*=NODAL，Abaqus 将使用分析中定义的任何取向（通过 [*TRANSFORM*](../key/key-link.md#usb-kws-mtransform) 选项）变换节点向量场。设置 *transformationType*=NODAL 对基于单元的结果没有影响。

如果 *transformationType*=USER_SPECIFIED，Abaqus 将把张量和向量场变换到由 *datumCsys* 指定的坐标系中。

如果 *transformationType*=LAYUP_ORIENTATION，Abaqus 将把张量和向量场变换到复合截面中定义的层合板取向。odb 需要包含字段 SORIENT 才能使用此选项。

*rigidTransformPrimary*

 Boolean，指定是否基于活动的用户特定系统对节点向量数据集执行刚性变换。默认值为 OFF。

*rigidTransformDeformed*

 Boolean，指定是否基于活动的用户特定系统对当前变形变量执行刚性变换。默认值为 OFF。

*transformOnDeformed*

 Boolean，指定是否在变换计算中考虑变形的影响。默认值为 ON。

*modelCanExtrude*

 Boolean，指定模型是否包含可以拉伸的任何单元或曲面。

*sweepModelType*

 Int，指定模型中包含的可扫描单元和曲面的类型（如果有）。

*averageElementOutput*

 Boolean，指定是否平均单元输出。默认值为 ON。

*averageOnlyDisplayed*

 Boolean，指定是否仅对显示的单元进行平均。默认值为 ON。

*regionBoundaries*

 SymbolicConstant，指定平均区域边界的类型。可选值为 NONE、ODB_REGIONS、ELEMENT_SET 和 DISPLAY_GROUPS。默认值为 ODB_REGIONS。

*useRegionBoundaries*

 Boolean，指定平均时是否使用区域边界。默认值为 ON。

*includeFeatureBoundaries*

 Boolean，指定是否基于特征边缘为壳和膜包含额外的平均边界。默认值为 ON。

*numSectors*

 Int，指定循环对称模型的扇区数。该值从循环对称模型自动计算。此值为只读。

*sectorAngle*

 Float，指定循环对称模型的扇区角度。该值从循环对称模型自动计算。此值为只读。

*automaticExtrudeDepth*

 Float，指定用于拉伸默认设置中的解析刚体的自动拉伸深度。此值为只读。

*cameraCsysName*

 String，指定驱动移动摄像头的坐标系名称。

*noResultsColor*

 String，指定没有结果的单元的颜色。默认值为 "White"。

*mirrorCsysName*

 SymbolicConstant GLOBAL 或 String，指定镜像坐标系的名称。默认值为 GLOBAL。

*patternCsysName*

 SymbolicConstant GLOBAL 或 String，指定图案坐标系的名称。默认值为 GLOBAL。

*datumCsys*

 [DatumCsys](pt01ch15pyo03.md) 对象，指定当 *transformationType*=USER_SPECIFIED 时用于结果变换的坐标系。

*selectedSectorNumbers*

 Int 元组，指定当 *sectorSelectionType*=SELECT_BY_NUMBER 时要显示的扇区。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *selectedSectorNumbers* ![](../graphics/ker_eqn00013.gif) 扇区数。默认值为 (1)。

*userRegions*

字符串元组，指定定义平均区域边界的单元集或显示组名称（取决于 `regionBoundaries` 的值）。默认值为空序列。

