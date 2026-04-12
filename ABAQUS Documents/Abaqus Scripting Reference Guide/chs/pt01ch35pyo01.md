# 35.1 OdbDisplay 对象

OdbDisplay 对象存储视口中输出数据库的上下文。OdbDisplay 对象没有构造函数。当您导入 Visualization 模块时，Abaqus 会创建 *defaultOdbDisplay* 成员。创建视口时，Abaqus 会创建 *odbDisplay* 成员，使用先前活动视口的属性。先前活动视口包含会话的 *defaultOdbDisplay* 对象的属性。*defaultOdbDisplay* 对象的属性从先前活动视口复制以创建新视口。

OdbDisplay 对象通过两种方式之一访问：
- 默认输出数据库显示选项。创建其他 *odbDisplay* 成员时使用这些设置作为默认值，可以设置这些值以自定义用户首选项。
- 与特定视口关联的输出数据库显示选项。

**访问**

```
session.viewports[*name*].layers[*name*].odbDisplay
import visualization
session.viewports[*name*].odbDisplay
```

### 35.1.1 moveCameraToCsys()

此方法指定摄像机的新位置。仅当 *movieMode*=ON（在 [View](pt01ch54pyo01.md) 对象中）时此方法才可用。新摄像机位置是由 [BasicOptions](pt01ch40pyo01.md) 对象的 *cameraCsysName* 成员指定的坐标系的原点。

**参数**

无。

**返回值**

无

**异常**

无。

### 35.1.2 setDeformedVariable(...)

此方法指定显示模型变形形状时使用的场输出变量或 FieldOutput 对象。

**必要参数**

必须提供以下两个互斥参数之一：

*variableLabel*

一个字符串，指定场输出变量。

*field*

一个字符串，指定 [FieldOutput](pt01ch34pyo06.md) 对象。

**可选参数**

无。

**返回值**

无

**异常**

如果视口未与任何 Odb 对象关联：

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.3 setFrame(...)

此方法指定 OdbDisplay 对象的步骤和帧。

**必要参数**

*step*

一个整数，指定步骤索引。可能的值为 0 ![](../graphics/ker_eqn00013.gif) *step* ![](../graphics/ker_eqn00013.gif) (*numSteps * 1)。

*frame*

一个整数，指定指定步骤中的帧。有效值为 0 ![](../graphics/ker_eqn00013.gif) *frame* ![](../graphics/ker_eqn00013.gif) (*numFramesInStep * 1)。如果 *frame* ![](../graphics/ker_eqn00407.gif) (*numFramesInStep * 1)，将显示最后一帧。

**可选参数**

无。

**返回值**

无

**异常**

如果视口未与任何 Odb 对象关联：

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

如果 Odb 对象不包含有效的步骤数据：

```
There are no valid step data on the odb. Requested operation cancelled.
```

如果传入无效的步骤索引作为参数：

```
Invalid step index:step.  Available step indices: 0 - n
```

### 35.1.4 setFrame(...)

此方法指定 OdbDisplay 对象的帧。

**必要参数**

*frame*

一个 OdbFrame 对象。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 35.1.5 setPrimaryVariable(...)

此方法指定要获取结果的场输出变量。

**必要参数**

*variableLabel*

一个字符串，指定场输出变量。*variableLabel* 和 *field* 参数互斥。

*field*

一个字符串，指定 FieldOutput 对象。*variableLabel* 和 *field* 参数互斥。

*outputPosition*

一个 SymbolicConstant，指定获取数据的位置。可能的值为 NODAL、INTEGRATION_POINT、ELEMENT_FACE、ELEMENT_NODAL、ELEMENT_CENTROID、WHOLE_ELEMENT、WHOLE_REGION、WHOLE_PART_INSTANCE、WHOLE_MODEL 和 GENERAL_PARTICLE。数据只能从分析期间写入输出数据库的位置获取。

**可选参数**

*refinement*

一个 SymbolicConstant 和一个字符串的序列。SymbolicConstant 的可能值为 INVARIANT 和 COMPONENT。该字符串为指定 *variableLabel* 指定可用的分量或不变量。仅当指定 *variableLabel* 有可用的细化时，才需要此参数。

*sectionPoint*

具有字符串键和字符串值的字典。每个键指定模型中的一个区域；对应的值指定该区域内的截面点。例如：

```
sectionPoint={'shell < MAT > < 7 section points >':'SPOS,
    (fraction = 1.0)', 'shell < MAT > < 5 section points >':
    'SPOS, (fraction = 1.0)', }
```

**返回值**

无

**异常**

如果视口未与任何 Odb 对象关联：

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.6 setPrimarySectionPoint(...)

此方法指定当前主要变量、符号变量和状态变量的截面点。

**必要参数**

*sectionPoint*

具有字符串键和字符串值的字典。每个键指定模型中的一个区域；对应的值指定该区域内的截面点。例如：

```
sectionPoint={'shell < MAT > < 7 section points >':'SPOS,
    (fraction = 1.0)', 'shell < MAT > < 5 section points >':
    'SPOS, (fraction = 1.0)', }
```

*activePly*

一个字符串，指定活动层名称。

**可选参数**

无。

**返回值**

无

**异常**

如果视口未与任何 Odb 对象关联：

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.7 setStatusVariable(...)

此方法指定用于基于状态标准过滤元素显示的场输出变量。

**必要参数**

*variableLabel*

一个字符串，指定场输出变量。*variableLabel* 和 *field* 参数互斥。

*field*

一个字符串，指定 FieldOutput 对象。*variableLabel* 和 *field* 参数互斥。

*outputPosition*

一个 SymbolicConstant，指定获取数据的位置。可能的值为 NODAL、INTEGRATION_POINT、ELEMENT_FACE、ELEMENT_NODAL、ELEMENT_CENTROID、WHOLE_ELEMENT、WHOLE_REGION、WHOLE_PART_INSTANCE、WHOLE_MODEL 和 GENERAL_PARTICLE。数据只能从分析期间写入输出数据库的位置获取。

**可选参数**

*refinement*

一个 SymbolicConstant 和一个字符串的序列。SymbolicConstant 的可能值为 INVARIANT 和 COMPONENT。该字符串为指定 *variableLabel* 指定可用的分量或不变量。仅当指定 *variableLabel* 有可用的细化时，才需要此参数。

*sectionPoint*

具有字符串键和字符串值的字典。每个键指定模型中的一个区域；对应的值指定该区域内的截面点。例如：

```
sectionPoint={'shell < MAT > < 7 section points >':'SPOS,
    (fraction = 1.0)', 'shell < MAT > < 5 section points >':
    'SPOS, (fraction = 1.0)', }
```

*statusMinimum*

一个 Float，指定要考虑用于元素移除的最小结果值。

*statusMaximum*

一个 Float，指定要考虑用于元素移除的最大结果值。

*statusInsideRange*

当同时给出 *statusMinimum* 和 *statusMaximum* 时使用的布尔值。为真时，包含最小值和最大值（含）之间值的元素将被移除。为假时，包含最小值和最大值（不含）之外值的元素将被移除。

*useStatus*

一个布尔值，指定是否激活状态变量。

*applyStatusToUndeformed*

一个布尔值，指定活动状态变量是否从未变形图中移除元素。默认值为 False。

**返回值**

无

**异常**

如果视口未与任何 Odb 对象关联：

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.8 setSymbolVariable(...)

此方法指定要获取用于符号绘图的结果的场输出变量。此变量必须以向量或张量数据的形式提供。输出量也可以使用此命令指定，以控制结果或分量的显示。

**必要参数**

*variableLabel*

一个字符串，指定场输出变量。*variableLabel* 和 *field* 参数互斥。

*field*

一个字符串，指定 FieldOutput 对象。*variableLabel* 和 *field* 参数互斥。

*outputPosition*

一个 SymbolicConstant，指定获取数据的位置。可能的值为 NODAL、INTEGRATION_POINT、ELEMENT_FACE、ELEMENT_NODAL、ELEMENT_CENTROID、WHOLE_ELEMENT、WHOLE_REGION、WHOLE_PART_INSTANCE、WHOLE_MODEL 和 GENERAL_PARTICLE。数据只能从分析期间写入输出数据库的位置获取。

**可选参数**

*refinement*

一个 SymbolicConstant 和一个字符串的序列。SymbolicConstant 的可能值为 INVARIANT 和 COMPONENT。该字符串为指定 *variableLabel* 指定可用的分量或不变量。仅当指定 *variableLabel* 有可用的细化时，才需要此参数。

*sectionPoint*

具有字符串键和字符串值的字典。每个键指定模型中的一个区域；对应的值指定该区域内的截面点。例如：

```
sectionPoint={'shell < MAT > < 7 section points >':'SPOS,
    (fraction = 1.0)', 'shell < MAT > < 5 section points >':
    'SPOS, (fraction = 1.0)', }
```

*tensorQuantity*

一个 SymbolicConstant，指定要与符号一起显示的张量 quantity。此值在 [SymbolOptions](pt01ch35pyo08.md) 对象中设置。

*vectorQuantity*

一个 SymbolicConstant，指定要与符号一起显示的向量 quantity。此值在 [SymbolOptions](pt01ch35pyo08.md) 对象中设置。

**返回值**

无

**异常**

如果视口未与任何 Odb 对象关联：

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.9 setStreamVariable(...)

此方法指定要获取用于流绘图的结果的场输出变量。此变量必须以节点向量数据的形式提供。

**必要参数**

*variableLabel*

一个字符串，指定场输出变量。

**可选参数**

无。

**返回值**

无

**异常**

如果视口未与任何 Odb 对象关联：

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.10 setValues(...)

此方法为 OdbDisplay 对象指定成员值。

**必要参数**

无。

**可选参数**

*visibleDisplayGroups*

[DisplayGroup](pt01ch16pyo01.md) 对象列表。

*viewCut*

一个布尔值，指定是否显示切割。默认值为 OFF。

*viewCutNames*

[ViewCut](pt01ch35pyo09.md) 对象列表。

**返回值**

无

**异常**

无。

### 35.1.11 成员

OdbDisplay 对象可以具有以下成员：

*name*

一个字符串，指定与 OdbDisplay 对象关联的输出数据库的名称。

*fieldSteps*

字符串元组，指定场步骤。

序列中的每个项目包含以下步骤信息：
- *element0*：一个字符串，指定步骤名称。
- *element1*：一个字符串，指定步骤描述。
- *element2*：一个 Float，指定步骤开始时的时间值。
- *element3*：一个 Float，指定步骤的时间周期。
- *element4*：一个 Float，指定用户修改的步骤时间周期。
- *element5*：一个 Int，指定步骤的域类型。可能的值为：- 0: 时间域- 1: 频率域- 2: 模态域- 3: 弧长（Riks）域
- *element6*：一个字符串，指定默认帧标签。
- *element7*：字符串序列，指定步骤中所有可用帧的帧标签。
- *element8*：浮点数序列，指定步骤中所有可用帧的帧值。
- *element9*：一个 Int，指定步骤是否为用户定义。可能的值为 0，表示步骤在分析中定义；1，表示步骤是用户定义的。
- *element10*：机器可读字符串序列，编码当前活动帧编号。

*fieldVariables*

一个 [OdbFieldVarList](pt01ch23pyo03.md) 对象。

*modelVariableList*

一个 [OdbModelFieldVarList](pt01ch23pyo04.md) 对象。

*nodeSet*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定集合标签。仓库是只读的。

*elementSet*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定集合标签。仓库是只读的。

*surfaceSet*

[OdbSet](pt01ch34pyo23.md) 对象仓库，指定集合标签。仓库是只读的。

*display*

一个 [DisplayOptions](pt01ch40pyo04.md) 对象。

*contourOptions*

一个 [ContourOptions](pt01ch35pyo03.md) 对象。

*commonOptions*

一个 [CommonOptions](pt01ch35pyo02.md) 对象。

*symbolOptions*

一个 [SymbolOptions](pt01ch35pyo08.md) 对象。

*superimposeOptions*

一个 [SuperimposeOptions](pt01ch35pyo07.md) 对象。

*displayBodyOptions*

一个 [DisplayBodyOptions](pt01ch35pyo05.md) 对象。

*freeBodyOptions*

一个 [FreeBodyOptions](pt01ch40pyo06.md) 对象。

*streamOptions*

一个 [StreamOptions](pt01ch40pyo21.md) 对象。

*viewCutOptions*

一个 [ViewCutOptions](pt01ch40pyo24.md) 对象。

*viewCuts*

[ViewCut](pt01ch35pyo09.md) 对象仓库。

*displayGroup*

一个 [DisplayGroup](pt01ch16pyo01.md) 对象，指定当前显示组并引用 [Session](pt01ch47pyo01.md) 的 *displayGroups* 成员中的对象。

*displayGroupInstances*

一个 [DisplayGroupInstanceRepository](pt01ch16pyo03.md) 对象。

*basicOptions*

一个 [BasicOptions](pt01ch40pyo01.md) 对象。

*materialOrientationOptions*

一个 [OrientationOptions](pt01ch35pyo06.md) 对象。

*fieldFrame*

字符串元组，指定当当前步骤为用户定义时的步骤标签和帧标签。或者，当当前步骤在分析中定义时，*fieldFrame* 可以指定为步骤索引和帧索引的对。

*primaryVariable*

指定变量的元组。

序列中的每个项目包含以下元素：
- 元素 0：一个字符串，指定变量标签。
- 元素 1：一个 Int，指定输出位置。可能的整数值为：- 0: UNDEFINED_POSITION- 1: NODAL- 2: INTEGRATION_POINT- 3: ELEMENT_FACE- 4: ELEMENT_NODAL- 5: WHOLE_ELEMENT- 6: ELEMENT_CENTROID- 7: WHOLE_REGION- 8: WHOLE_PART_INSTANCE- 9: WHOLE_MODEL- 10: GENERAL_PARTICLE
- 元素 2：一个 Int，指定数据类型。可能的值为：- 0: ENUMERATION- 1: BOOLEAN- 2: INTEGER- 3: SCALAR- 4: VECTOR- 5: QUATERNION_2D- 6: QUATERNION_3D- 7: TENSOR- 8: TENSOR_3D_FULL- 9: TENSOR_3D_PLANAR- 10: TENSOR_3D_SURFACE- 11: TENSOR_2D_PLANAR- 12: TENSOR_2D_SURFACE
- 元素 3：一个 Int，指定存储类型。可能的值为：- 0: FLOAT- 1: DOUBLE- 2: INTEGER- 3: BOOLEAN
- 元素 4：一个 Int，指定细化类型。可能的值为：- 0: NO_REFINEMENT- 1: INVARIANT- 2: COMPONENT
- 元素 5：一个字符串，指定细化标签。
- 元素 6：一个 Int，指定细化索引。
- 元素 7：一个 Int，指定截面点信息是否可用。截面点信息可用时为 1；此信息不可用时为 0。
- 元素 8：一个字符串序列，指定层名称和类别选择元组（见下文），指定截面点信息。类别选择元组由以下元素组成：- 元素 0：一个字符串，指定类别标签。- 元素 1：一个 Int，指定是否使用顶部和底部截面点来获取结果。使用两个截面点时为 1，仅使用顶部截面点时为 0。- 元素 2：一个 Int，指定顶部截面点索引。- 元素 3：一个字符串，指定顶部截面标签。- 元素 4：一个 Int，指定底部截面点索引。- 元素 5：一个字符串，指定底部截面标签。- 元素 6：一个 Int，指定类别 ID。
- 元素 9：一个 Int，指定数据是否为复数。数据为复数时为 1；数据不为复数时为 0。
- 元素 10：一个 Float，指定数据的最小可能值。
- 元素 11：一个 Float，指定数据的最大可能值。
- 元素 12：一个 Int，指定数据是否为派生。数据为派生时为 1；数据不为派生时为 0。

*deformedVariable*

指定变量的元组。

有关序列的信息，请参阅成员 *primaryVariable*。

*statusVariable*

指定变量的 SymbolicConstant 元组。

有关序列的信息，请参阅成员 *primaryVariable*。

*symbolVariable*

指定变量的 SymbolicConstant 元组。

有关序列的信息，请参阅成员 *primaryVariable*。

*applyStatusToUndeformed*

指定布尔值的 SymbolicConstant 元组，指定是否基于活动状态变量在未变形状态下移除元素。

*statusInsideRange*

指定布尔值的 SymbolicConstant 元组，指定状态范围是否应在指定的最小值和最大值之内。当为假时，范围将在外部。

*statusMinimum*

指定最小状态范围值的 Float 值的 Float 元组。

*statusMaximum*

指定最大状态范围值的 Float 值的 Float 元组。

*useStatus*

指定布尔值的 SymbolicConstant 元组，指定是否基于状态变量移除元素。

*firstFrame*

指定第一个可用帧的步骤索引和帧索引的整数对。此序列是只读的。

*prevFrame*

指定当前帧之前一帧的步骤索引和帧索引的整数对。此序列是只读的。

*nextFrame*

指定当前帧之后一帧的步骤索引和帧索引的整数对。此序列是只读的。

*lastFrame*

指定最后一个可用帧的步骤索引和帧索引的整数对。此序列是只读的。
