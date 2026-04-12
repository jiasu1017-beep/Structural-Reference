# 48.1 ConstrainedSketch 对象





ConstrainedSketch 对象包含用于创建草图的实体。这些对象包括几何存储库中的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象，如 Line、Arc 和 Spline。Vertex、Dimension、Constraint 和 Parameter 对象包含在各自的存储库中。

**访问**

```
import sketch
mdb.models[*name*].sketches[*name*]
```

### 48.1.1 ConstrainedSketch(...)

此方法创建 ConstrainedSketch 对象。如果无法创建草图，则该方法返回 `None`。

**路径**

```
mdb.models[*name*].ConstrainedSketch
```

**必要参数**

*name*

String，指定存储库键。

*sheetSize*

Float，指定图纸大小。

**可选参数**

*gridSpacing*

Float，指定网格线之间的间距。可能的值为 Floats ![](../graphics/ker_eqn00060.gif) 0。默认值为 *sheetSize* 的约 2%。

*transform*

Floats 序列的序列，指定草图的三维方向。该序列是一个 3×4 变换矩阵，指定旋转轴和平移向量。可能的值为任何 Floats。

旋转轴的默认值是单位矩阵

```
(1.0, 0.0, 0.0),  (0.0, 1.0, 0.0),  (0.0, 0.0, 1.0)
```

平移向量的默认值是

```
(0.0, 0.0, 0.0)
```

默认值将草图定位在原点中心的 X–Y 平面上。

**返回值**

ConstrainedSketch 对象。

**异常**

无。

### 48.1.2 ConstrainedSketch(...)

此方法将一个 ConstrainedSketch 对象复制到一个新的 ConstrainedSketch 对象。

**注意：**如果要被复制的草图名称是 `__edit__`，Abaqus 会创建一个包含参考几何和非恒等变换矩阵的精确副本。否则，`Sketch` 复制构造函数会从复制的草图中剥离参考几何，并将变换矩阵设置为恒等矩阵，创建一个独立副本。

**路径**

```
mdb.models[*name*].ConstrainedSketch
```

**必要参数**

*name*

String，指定存储库键。

*objectToCopy*

要被复制的 ConstrainedSketch 对象。

**可选参数**

无。

**返回值**

ConstrainedSketch 对象。

**异常**

InvalidNameError。

### 48.1.3 ConstrainedSketchFromGeometryFile(...)

此方法创建 ConstrainedSketch 对象并将其放入 `sketches` 存储库。

**路径**

```
mdb.models[*name*].ConstrainedSketchFromGeometryFile
```

**必要参数**

*name*

String，指定存储库键。

*geometryFile*

[AcisFile](pt01ch37pyo03.md) 对象，指定包含几何的文件。文件中的几何被转换为 X–Y 平面中的二维草图几何。

**可选参数**

无。

**返回值**

ConstrainedSketch 对象。

**异常**

InvalidNameError。

### 48.1.4 print()

此方法打印有关草图的以下统计信息：
- 草图 Id（一个正整数）。
- 几何曲线数（[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象数）。
- 尺寸数（[ConstrainedSketchDimension](pt01ch48pyo03.md) 对象数）。
- 顶点数（[ConstrainedSketchVertex](pt01ch48pyo10.md) 对象数）。

**参数**

无。

**返回值**

无

**异常**

无。

### 48.1.5 assignCenterline(...)

此方法指示将用作旋转特征中心线的构造线。

**必要参数**

*line*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象，指定指示旋转特征中心线的构造线。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.6 assignCenterOfTwist(...)

此方法指示当使用扭曲创建拉伸特征时将使用的孤立点作为扭曲中心。

**必要参数**

*point*

[ConstrainedSketchVertex](pt01ch48pyo10.md) 对象，指定指示使用扭曲角度的拉伸特征的扭曲中心的孤立点。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.7 autoDimension(...)

此方法对所选的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象应用尺寸，努力使 ConstrainedSketch 明确定义。

**必要参数**

*objectList*

序列，指定要标注尺寸的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.8 autoTrimCurve(...)

此方法在指定位置自动修剪所选的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象。如果对象不与其他 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象相交，则整个所选对象将被删除。

**必要参数**

*curve1*

要被修剪的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象。

*point1*

Floats 对，指定要应用修剪的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 上的位置。*point1* 和 *parameter1* 互斥。

*parameter1*

Float，指定要应用修剪的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 上的参数位置。*point1* 和 *parameter1* 互斥。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.9 breakCurve(...)

此方法使用另一个指定的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象（*curve2*）断开指定的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象（*curve1*）。如果所选的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象相交，则只会断开 *curve1*；*curve2* 不受操作影响。断点位置由指定的点值决定。

**必要参数**

*curve1*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象，指定要被断开的对象。

*point1*

Floats 对，指定 *curve1* 上要应用断开的大致位置。

*curve2*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象，指定 *curve1* 应该在何处断开。

*point2*

Floats 对，指定 *curve2* 上 *curve1* 应该断开的大致位置。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.10 copyMirror(...)

此方法创建给定 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象的副本，关于所选线镜像，并将它们插入 ConstrainedSketch 对象的相应存储库中。

**必要参数**

*mirrorLine*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象，指定 Abaqus 将围绕其镜像草图的线。

*objectList*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列，指定要被复制和镜像的草图。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.11 copyMove(...)

此方法创建给定 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象的副本，从原始位置移动它们，并将它们插入 ConstrainedSketch 对象的相应存储库中。

**必要参数**

*vector*

两个 Floats 的序列，指定平移向量。

*objectList*

要被复制和移动的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.12 copyRotate(...)

此方法创建给定 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象的副本，旋转它们，并将它们插入 ConstrainedSketch 对象的相应存储库中。

**必要参数**

*centerPoint*

Floats 对，指定旋转中心。

*angle*

Float，指定旋转角度（度）。

*objectList*

要被复制和移动的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.13 copyScale(...)

此方法创建给定 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象的副本，关于所选点按指定值缩放它们，并将它们插入 ConstrainedSketch 对象的相应存储库中。

**必要参数**

*scaleValue*

Float，指定缩放值。

*scaleCenter*

Floats 对，指定缩放中心。

*objectList*

要被复制和缩放的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.14 delete(...)

此方法删除给定的 [ConstrainedSketchGeometry](pt01ch48pyo05.md)、[ConstrainedSketchDimension](pt01ch48pyo03.md) 或 [ConstrainedSketchConstraint](pt01ch48pyo02.md) 对象。

**必要参数**

*objectList*

要被删除的 [ConstrainedSketchGeometry](pt01ch48pyo05.md)、[ConstrainedSketchDimension](pt01ch48pyo03.md) 或 [ConstrainedSketchConstraint](pt01ch48pyo02.md) 对象序列。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.15 deleteParameter(...)

此命令删除指定参数。

**必要参数**

*name*

String，指定要删除的参数名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.16 dragEntity(...)

此方法将指定的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 或 [ConstrainedSketchVertex](pt01ch48pyo10.md) 对象拖动到特定位置。

**必要参数**

*entity*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 或 [ConstrainedSketchVertex](pt01ch48pyo10.md) 对象，指定要拖动的对象。

*points*

三个 Floats 序列的序列，指定沿其拖动实体的点序列。序列中点的顺序定义了一条路径，该路径决定解。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.17 linearPattern(...)

此方法沿一个或两个方向以线性图案复制 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象。此方法还复制所选对象之间存在的任何关联尺寸或约束对象。

**必要参数**

*number1*

Integer，指定沿图案第一个方向出现的副本总数（包括原始对象）。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *number1* ![](../graphics/ker_eqn00013.gif) 1000。

*spacing1*

Float，指定沿图案第一个方向副本之间的间距。可能的值为 0.0 ![](../graphics/ker_eqn00419.gif) *spacing1*。

*angle1*

Float，指定图案第一个方向的角度（度）。可能的值为 –360.0 ![](../graphics/ker_eqn00013.gif) *angle1* ![](../graphics/ker_eqn00013.gif) 360.0。

**可选参数**

*vertexList*

要复制的 [ConstrainedSketchVertex](pt01ch48pyo10.md) 对象序列。

*geomList*

要复制的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列。

*number2*

Integer，指定沿图案第二个方向出现的副本总数（包括原始对象）。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *number2* ![](../graphics/ker_eqn00013.gif) 1000。默认值为 1。*number1* 或 *number2* 中至少有一个必须大于一。

*spacing2*

Float，指定沿图案第一个方向副本之间的间距。可能的值为 0.0 ![](../graphics/ker_eqn00419.gif) *spacing2*。默认值为 *spacing1*。

*angle2*

Float，指定图案第一个方向的角度（度）。可能的值为 –360.0 ![](../graphics/ker_eqn00013.gif) *angle2* ![](../graphics/ker_eqn00013.gif) 360.0。默认值为比 *angle1* 大 90 度。

**返回值**

无

**异常**

AbaqusException

```
Number must be greater than 1 for at least one direction
```

### 48.1.18 mergeVertices(...)

此方法合并位于彼此指定距离内的 [ConstrainedSketchVertex](pt01ch48pyo10.md) 对象。如果只选择一个 [ConstrainedSketchVertex](pt01ch48pyo10.md) 对象，它将合并位于该顶点指定距离内的所有 [ConstrainedSketchVertex](pt01ch48pyo10.md) 对象。如果选择多个顶点，搜索将仅限制在所选的 [ConstrainedSketchVertex](pt01ch48pyo10.md) 对象内。

**必要参数**

*value*

Float，指定搜索半径。

*vertexList*

要被合并的 [ConstrainedSketchVertex](pt01ch48pyo10.md) 对象序列。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.19 move(...)

此方法通过给定向量平移给定的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象。

**必要参数**

*vector*

两个 Floats 的序列，指定平移向量。

*objectList*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列，指定要被平移的对象。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.20 offset(...)

此方法创建所选 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象的副本，按指定距离在指定方向偏移它们，并将它们插入 ConstrainedSketch 对象的相应存储库中。如果选择了连接的对象，则执行修剪或延伸以完成偏移。

**必要参数**

*distance*

Float，指定偏移距离。

*objectList*

要被复制和偏移的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列。

*side*

SymbolicConstant，指定偏移发生的侧。可能的值为 LEFT 和 RIGHT。

**可选参数**

*filletCorners*

Boolean，指定角落是否需要倒圆而不是延伸。

**返回值**

无

**异常**

无。

### 48.1.21 radialPattern(...)

此方法关于指定中心点以径向图案复制 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象。

**必要参数**

*number*

Int，指定径向图案中出现的副本总数（包括原始对象）。可能的值为 2 ![](../graphics/ker_eqn00013.gif) *number2* ![](../graphics/ker_eqn00013.gif) 1000。

*totalAngle*

Float，指定图案中第一个和最后一个实例之间的总角度（度）。正角度对应逆时针方向。值 360 和 -360 代表一种特殊情况，即图案完整一圈。在这种情况下，由于副本将覆盖原始对象，因此不会放置在最后位置。可能的值为 –360.0 ![](../graphics/ker_eqn00013.gif) *totalAngle* ![](../graphics/ker_eqn00013.gif) 360.0。

*centerPoint*

Floats 对，指定径向图案的中心。

**可选参数**

*vertexList*

要复制的 [ConstrainedSketchVertex](pt01ch48pyo10.md) 对象序列。

*geomList*

要复制的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列。

**返回值**

无

**异常**

无。

### 48.1.22 resetView()

此方法将视图重置为垂直于绘图平面。

**参数**

无。

**返回值**

无

**异常**

无。

### 48.1.23 rectangle(...)

此方法创建四条线，形成由给定点的对角角定义的矩形，并将它们插入 ConstrainedSketch 对象的 `geometry` 存储库中。

**必要参数**

*point1*

Floats 对，指定矩形的第一个角。

*point2*

Floats 对，指定矩形的第二个角。

**可选参数**

无。

**返回值**

Int，指定方法的成功或失败。值 0 表示失败。

**异常**

无。

### 48.1.24 removeGapsAndOverlaps(...)

此方法移除用户指定的草图几何之间的间隙和重叠。此方法在清理导入的草图时特别有用。

**必要参数**

*tolerance*

Float 值，指定要移除的实体之间间隙或重叠的最大尺寸。通常此值很小，用于关闭可能在原始程序中不存在但由于两个程序之间的公差不匹配而存在于草图中的间隙和重叠。

*geomList*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列，指定要移除间隙和重叠的位置。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.25 repairShortEdges(...)

此方法删除指定的短边，可选地仅选择长度小于指定公差的那些短边，并修复草图中由此产生的间隙。此方法在清理导入的草图时与 `removeGapsAndOverlap` 结合使用特别有用。

**必要参数**

*geomList*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列，指定要移除短边的位置。

**可选参数**

*tolerance*

Float 值，用于选择和删除 *geomList* 中长度小于给定值的那些边。默认值为 –1.0。此值意味着 *geomList* 中指定的所有边都将被移除，并修复草图以移除由其移除留下的间隙。

**返回值**

无

**异常**

无。

### 48.1.26 retrieveSketch(...)

此方法从指定的 ConstrainedSketch 对象复制所有 [ConstrainedSketchGeometry](pt01ch48pyo05.md)、[ConstrainedSketchDimension](pt01ch48pyo03.md)、[ConstrainedSketchConstraint](pt01ch48pyo02.md) 和 [ConstrainedSketchParameter](pt01ch48pyo09.md) 对象。新对象被添加到现有对象（如果有）。指定 ConstrainedSketch 对象中的对象不会被检索操作修改。

**必要参数**

*sketch*

ConstrainedSketch 对象，指定要从中复制的对象。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.27 rotate(...)

此方法将给定的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象围绕给定点和给定角度旋转。

**必要参数**

*centerPoint*

Floats 对，指定旋转中心。

*angle*

Float，指定旋转角度（度）。

*objectList*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 序列，指定要被旋转的对象。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.28 scale(...)

此方法将给定的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象关于给定点和给定比例因子进行缩放。

**必要参数**

*scaleValue*

Float，指定缩放值。

*scaleCenter*

Floats 对，指定缩放中心。

*objectList*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象序列，指定要被缩放的对象。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.29 setPrimaryObject(...)

此方法使 ConstrainedSketch 对象成为当前视口中的主对象。草图保持作为当前视口中的主对象，直到发出 `unsetPrimaryobject` 命令。

**必要参数**

*option*

SymbolicConstant，指定如何显示草图。可能的值为：
- STANDALONE：指示新的独立草图。当前视口被清除并被独立草图取代。视图方向设置为 ![](../graphics/ker_eqn00085.gif)。
- SUPERIMPOSE：指示草图叠加在当前视口上。视图方向变为垂直于草图平面。更改以动画序列的许多小视图步骤平滑生效。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.30 trimExtendCurve(...)

此方法使用另一个指定的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象（*curve2*）修剪或延伸指定的 [ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象（*curve1*）。*curve2* 不受操作影响。修剪或延伸的位置由指定的点值决定。

**必要参数**

*curve1*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象，指定要被修剪或延伸的对象。

*point1*

Floats 对，指定 *curve1* 上要应用修剪或延伸的位置。

*curve2*

[ConstrainedSketchGeometry](pt01ch48pyo05.md) 对象，指定 *curve1* 被修剪或延伸到的对象。*curve2* 不会被修剪或延伸。

*point2*

Floats 对，指定 *curve2* 上 *curve1* 应该被修剪或延伸的大致位置。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 48.1.31 undo()

此方法撤销最后一个 ConstrainedSketch 对象方法的效果。

**参数**

无。

**返回值**

无

**异常**

无。

### 48.1.32 unsetPrimaryObject()

此方法从当前视口移除 ConstrainedSketch 对象，逆转 `setPrimaryobject` 命令的效果。如果 *option* 参数设置为 SUPERIMPOSE，则视口将返回到发出 `setPrimaryobject` 命令时存在的视图方向。如果 *option* 参数设置为 STANDALONE，则视口将留空。

**参数**

无。

**返回值**

无

**异常**

无。

### 48.1.33 writeAcisFile(...)

此方法将草图的几何导出为 ACIS 格式的命名文件。

**必要参数**

*fileName*

String，指定文件名。

**可选参数**

*version*

Float，指定 ACIS 版本。例如，Float "12.0" 对应 ACIS Version 12.0。默认值为当前版本的 ACIS。

**返回值**

无

**异常**

InvalidNameError。

### 48.1.34 writeIgesFile(...)

此方法将草图的几何导出为 IGES 格式的命名文件。

**必要参数**

*filename*

String，指定文件名。

**可选参数**

*flavor*

SymbolicConstant，指定要导出的特定 IGES 风格。可能的值为 STANDARD、AUTOCAD、SOLIDWORKS、JAMA 和 MSBO。

**返回值**

无

**异常**

InvalidNameError。

### 48.1.35 成员

ConstrainedSketch 对象可以具有以下成员：

*constraints*

[ConstrainedSketchConstraint](pt01ch48pyo02.md) 对象存储库。

*dimensions*

[ConstrainedSketchDimension](pt01ch48pyo03.md) 对象存储库。

*geometry*

[ConstrainedSketchGeometryArray](pt01ch48pyo05.md) 对象，指定草图几何，如线、弧、圆和样条曲线。

*parameters*

[ConstrainedSketchParameter](pt01ch48pyo09.md) 对象存储库，指定草图参数，这些参数可以与尺寸关联。

*sketchOptions*

[ConstrainedSketchOptions](pt01ch48pyo08.md) 对象，指定草图选项设置。

*vertices*

[ConstrainedSketchVertexArray](pt01ch48pyo10.md) 对象。

*imageOptions*

[ConstrainedSketchImageOptions](pt01ch48pyo07.md) 对象。


