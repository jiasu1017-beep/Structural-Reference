# 25.74 SurfaceToSurfaceContactExp 对象

SurfaceToSurfaceContactExp 对象在 Abaqus/Explicit 分析期间定义表面到表面接触。

SurfaceToSurfaceContactExp 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.74.1 SurfaceToSurfaceContactExp(...)

此方法创建一个 SurfaceToSurfaceContactExp 对象。

**路径**

```
mdb.models[*name*].SurfaceToSurfaceContactExp
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 SurfaceToSurfaceContactExp 对象的步骤名称。

*master*

[Region](pt01ch45pyo03.md) 对象，指定主表面。

*slave*

[Region](pt01ch45pyo03.md) 对象，指定从属表面。

*sliding*

 SymbolicConstant，指定接触公式。可能的值为 FINITE 和 SMALL。

*interactionProperty*

字符串，指定与此交互关联的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。

**可选参数**

*mechanicalConstraint*

 SymbolicConstant，指定机械约束公式。可能的值为 KINEMATIC 和 PENALTY。默认值为 KINEMATIC。

*weightingFactorType*

 SymbolicConstant，指定节点到面接触的加权。可能的值为 DEFAULT 和 SPECIFIED。默认值为 DEFAULT。

*weightingFactor*

浮点数，指定当 *weightingFactorType*=SPECIFIED 时接触表面的加权因子。默认值为 0.0。

*contactControls*

字符串，指定与此交互关联的 [ContactControl](pt01ch25pyo16.md) 对象的名称。空字符串表示将使用默认接触控制。默认值为空字符串。

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

**返回值**

SurfaceToSurfaceContactExp 对象。

**异常**

无。

### 25.74.2 swapSurfaces()

此方法切换表面到表面接触对的主表面和从属表面。此命令仅在创建交互的步骤中有效。

**参数**

无。

**返回值**

无。

**异常**

无。

### 25.74.3 setValues(...)

此方法修改创建 SurfaceToSurfaceContactExp 对象的步骤中现有 SurfaceToSurfaceContactExp 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SurfaceToSurfaceContactExp](pt01ch25pyo74.md#ker-surfacetosurfacecontactexp-surfacetosurfacecontactex-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.74.4 setValuesInStep(...)

此方法修改指定步骤中现有 SurfaceToSurfaceContactExp 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

*interactionProperty*

字符串，指定与此交互关联的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。

*contactControls*

字符串，指定与此交互关联的 [ContactControl](pt01ch25pyo16.md) 对象的名称。空字符串表示将使用默认接触控制。默认值为空字符串。

**返回值**

无。

**异常**

无。

### 25.74.5 成员

SurfaceToSurfaceContactExp 对象的成员与 [SurfaceToSurfaceContactExp](pt01ch25pyo74.md#ker-surfacetosurfacecontactexp-surfacetosurfacecontactex-pyc) 方法的参数具有相同的名称和描述。





