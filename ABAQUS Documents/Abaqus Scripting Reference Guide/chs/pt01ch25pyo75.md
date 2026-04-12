# 25.75 SurfaceToSurfaceContactStd 对象

SurfaceToSurfaceContactStd 对象在 Abaqus/Standard 分析期间定义表面到表面接触。

SurfaceToSurfaceContactStd 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.75.1 SurfaceToSurfaceContactStd(...)

此方法创建一个 SurfaceToSurfaceContactStd 对象。

**路径**

```
mdb.models[*name*].SurfaceToSurfaceContactStd
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 SurfaceToSurfaceContactStd 对象的步骤名称。

*master*

[Region](pt01ch45pyo03.md) 对象，指定主表面。

*slave*

[Region](pt01ch45pyo03.md) 对象，指定从属表面。

*sliding*

 SymbolicConstant，指定接触公式。可能的值为 FINITE 和 SMALL。

*interactionProperty*

字符串，指定与此交互关联的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。

**可选参数**

*interferenceType*

 SymbolicConstant，指定接触对和接触元素允许的时间相关干扰类型。可能的值为：
- NONE，指定不允许接触干扰。
- SHRINK_FIT。
- UNIFORM。

默认值为 NONE。

*overclosure*

浮点数，指定允许的最大过闭合距离。此参数仅在 *interferenceType*=UNIFORM 时适用。默认值为 0.0。

*interferenceDirectionType*

 SymbolicConstant，指定用于确定干扰方向的方法。可能的值为 COMPUTED 和 DIRECTION_COSINE。默认值为 COMPUTED。

*direction*

三个浮点数组成的序列，指定以下内容：
- ![](../graphics/ker_eqn00083.gif)-干扰方向向量的方向余弦。
- ![](../graphics/ker_eqn00084.gif)-干扰方向向量的方向余弦。
- ![](../graphics/ker_eqn00085.gif)-干扰方向向量的方向余弦。

此参数仅在 *interferenceDirectionType*=DIRECTION_COSINE 时需要。

*amplitude*

字符串，指定定义步骤中规定干扰大小的幅值曲线名称。使用 `None` 可以指定规定干扰在步骤开始时立即应用并在线性跨越步骤降为零。

*smooth*

浮点数，指定当 *enforcement*=NODE_TO_SURFACE 时涉及的变形或刚性主表面使用的平滑程度。值必须在 0.0 和 0.5 之间。默认值为 0.2。

*hcrit*

浮点数，指定从属节点在 Abaqus/Standard 放弃当前增量并使用更小增量重试之前必须侵入主表面的距离。默认值为 0.0。

*extensionZone*

浮点数，指定主表面延伸的端段或面元边缘长度的分数，以避免与接触建模相关的数值舍入误差。值必须在 0.0 和 0.2 之间。默认值为 0.1。

*adjustMethod*

 SymbolicConstant，指定调整方法。可能的值为 NONE、OVERCLOSED、TOLERANCE 和 SET。默认值为 NONE。

*adjustTolerance*

浮点数，指定调整容差。默认值为 0.0。

*adjustSet*

[Region](pt01ch45pyo03.md) 对象，指定要应用调整的 Set 对象。

*enforcement*

 SymbolicConstant，指定离散化方法。可能的值为 NODE_TO_SURFACE 和 SURFACE_TO_SURFACE。默认值为 SURFACE_TO_SURFACE。

*thickness*

布尔值，指定是否考虑壳/膜元素厚度。默认值为 ON。

当 *sliding*=FINITE 且 *enforcement*=NODE_TO_SURFACE 时，此参数无效。

*contactControls*

字符串，指定与此交互关联的 [ContactControl](pt01ch25pyo16.md) 对象的名称。空字符串表示将使用默认接触控制。默认值为空字符串。

*tied*

布尔值，指定表面是否在模拟持续时间内"绑定"在一起。默认值为 OFF。

*initialClearance*

 SymbolicConstant 或浮点数，指定接触区域处的初始间隙。可能的值为 OMIT 和 COMPUTED。默认值为 OMIT。

*halfThreadAngle*

 `None` 或浮点数序列，指定用于螺栓间隙的半螺纹角。默认值为 `None`。

*pitch*

 `None` 或浮点数序列，指定用于螺栓间隙的螺距。默认值为 `None`。

*majorBoltDiameter*

 SymbolicConstant COMPUTED 或浮点数，指定用于螺栓间隙的螺栓公称直径。默认值为 COMPUTED。

*meanBoltDiameter*

 SymbolicConstant COMPUTED 或浮点数，指定用于螺栓间隙的螺栓平均直径。默认值为 COMPUTED。

*datumAxis*

[DatumAxis](pt01ch15pyo02.md) 对象，指定指定螺栓间隙时螺栓孔的方向。

*useReverseDatumAxis*

布尔值，指定是否反转由基准轴给出的螺栓间隙方向。默认值为 OFF。

*clearanceRegion*

[Region](pt01ch45pyo03.md) 对象，指定指定间隙的接触区域。

*surfaceSmoothing*

 SymbolicConstant，指定是否为 SurfaceToSurfaceContactStd 交互中的几何表面使用表面平滑。可能的值为 AUTOMATIC 和 NONE。默认值为 NONE。

*bondingSet*

[Region](pt01ch45pyo03.md) 对象，指定用于绑定的从属节点子集，仅在接触属性 [CohesiveBehavior](pt01ch25pyo11.md) 选项指定使用时。

**返回值**

SurfaceToSurfaceContactStd 对象。

**异常**

无。

### 25.75.2 swapSurfaces()

此方法切换表面到表面接触对的主表面和从属表面。此命令仅在创建交互的步骤中有效。

**参数**

无。

**返回值**

无。

**异常**

无。

### 25.75.3 setValues(...)

此方法修改创建 SurfaceToSurfaceContactStd 对象的步骤中现有 SurfaceToSurfaceContactStd 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SurfaceToSurfaceContactStd](pt01ch25pyo75.md#ker-surfacetosurfacecontactstd-surfacetosurfacecontactst-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.75.4 setValuesInStep(...)

此方法修改指定步骤中现有 SurfaceToSurfaceContactStd 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

*interactionProperty*

字符串，指定与此交互关联的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。

*interferenceType*

 SymbolicConstant，指定接触对和接触元素允许的时间相关干扰类型。可能的值为：
- NONE，指定不允许接触干扰。
- SHRINK_FIT。
- UNIFORM。

默认值为 NONE。

*overclosure*

浮点数，指定允许的最大过闭合距离。此参数仅在 *interferenceType*=UNIFORM 时适用。默认值为 0.0。

*interferenceDirectionType*

 SymbolicConstant，指定用于确定干扰方向的方法。可能的值为 COMPUTED 和 DIRECTION_COSINE。默认值为 COMPUTED。

*direction*

三个浮点数组成的序列，指定以下内容：
- ![](../graphics/ker_eqn00083.gif)-干扰方向向量的方向余弦。
- ![](../graphics/ker_eqn00084.gif)-干扰方向向量的方向余弦。
- ![](../graphics/ker_eqn00085.gif)-干扰方向向量的方向余弦。

此参数仅在 *interferenceDirectionType*=DIRECTION_COSINE 时需要。

*amplitude*

字符串，指定定义步骤中规定干扰大小的幅值曲线名称。使用 `None` 可以指定规定干扰在步骤开始时立即应用并在线性跨越步骤降为零。

*contactControls*

字符串，指定与此交互关联的 [ContactControl](pt01ch25pyo16.md) 对象的名称。空字符串表示将使用默认接触控制。默认值为空字符串。

**返回值**

无。

**异常**

无。

### 25.75.5 成员

SurfaceToSurfaceContactStd 对象的成员与 [SurfaceToSurfaceContactStd](pt01ch25pyo75.md#ker-surfacetosurfacecontactstd-surfacetosurfacecontactst-pyc) 方法的参数具有相同的名称和描述。

此外，SurfaceToSurfaceContactStd 对象具有以下成员：

*contactTracking*

 SymbolicConstant，指定接触跟踪算法的选择。STATE 跟踪算法仅使用法向投影，通过使用 ONE_CONFIG 指定。PATH 跟踪算法使用交叉和法向投影，通过使用 TWO_CONFIG 指定。可能的值为 ONE_CONFIG 和 TWO_CONFIG。默认值为 TWO_CONFIG。

此参数仅在 *sliding*=FINITE 且 *enforcement*=SURFACE_TO_SURFACE 时有效。

*supplementaryContact*

 SymbolicConstant，指定中间面约束的使用方式。可能的值为 SELECTIVE、NEVER 和 ALWAYS。默认值为 SELECTIVE。

当 *sliding*=FINITE 且 *enforcement*=SURFACE_TO_SURFACE 时，此参数无效。



