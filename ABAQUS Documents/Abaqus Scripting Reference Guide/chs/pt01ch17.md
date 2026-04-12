# 17.1 AssemblyDisplayOptions 对象









AssemblyDisplayOptions 对象存储指定如何在特定视口中显示装配的设置。AssemblyDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
import assembly
session.viewports[*name*].assemblyDisplay
session.viewports[*name*].layers[*name*].assemblyDisplay
```

### 17.1.1 setValues(...)

此方法修改 AssemblyDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*visibleInstances*

一个 String 序列，指定在视口中可见的部件实例的名称。默认值为空序列。

*step*

一个 String，指定要显示对象的步骤。可能的值为任何有效的步骤名称。默认值为 "Initial"。

*renderStyle*

一个 SymbolicConstant，指定视口中图像的渲染方式。可能的值为 WIREFRAME、HIDDEN、SHADED 和 FILLED。默认值为 WIREFRAME。

*mesh*

一个 Boolean，指定是否显示网格。默认值为 OFF。

*loads*

一个 Boolean，指定是否显示载荷。默认值为 OFF。

*bcs*

一个 Boolean，指定是否显示边界条件。默认值为 OFF。

*interactions*

一个 Boolean，指定是否显示相互作用。默认值为 OFF。

*constraints*

一个 Boolean，指定是否显示约束。默认值为 OFF。

*connectors*

一个 Boolean，指定是否显示连接器。默认值为 OFF。

*cnxEndPoints*

一个 Boolean，指定是否显示连接器端点。此成员仅在 *connectors*=ON 时适用。默认值为 ON。

*cnxLocalAxes*

一个 Boolean，指定是否显示连接器局部坐标系轴。此成员仅在 *connectors*=ON 时适用。默认值为 ON。

*cnxTypeLabels*

一个 Boolean，指定是否显示连接器截面类型标签。此成员仅在 *connectors*=ON 时适用。默认值为 ON。

*cnxTagDisplay*

一个 Boolean，指定是否在连接器截面类型标签旁显示标签信息。此成员仅在 *connectors*=ON 且 *cnxTypeLabels*=ON 时适用。默认值为 OFF。

*predefinedFields*

一个 Boolean，指定是否显示场和初始条件。默认值为 OFF。

*visibleDisplayGroups*

一个 [DisplayGroup](pt01ch16pyo01.md) 对象序列，指定在视口中可见的 DisplayGroups。当前该序列最多可包含一个 [DisplayGroup](pt01ch16pyo01.md) 对象。默认值为空序列。

*engineeringFeatures*

一个 Boolean，指定是否显示工程特征。默认值为 OFF。

*renderBeamProfiles*

一个 Boolean，指定是否渲染梁截面。默认值为 OFF。

*beamScaleFactor*

一个 Float，指定梁截面比例因子。beamScaleFactor 必须大于零。默认值为 1.0。

*optimizationTasks*

一个 Boolean，指定是否显示优化任务。默认值为 OFF。

*geometricRestrictions*

一个 Boolean，指定是否显示几何约束。默认值为 OFF。

*stopConditions*

一个 Boolean，指定是否显示停止条件。默认值为 OFF。

**返回值**

无

**异常**

RangeError。

### 17.1.2 成员

AssemblyDisplayOptions 对象可具有以下成员：

*bcs*

一个 Boolean，指定是否显示边界条件。默认值为 OFF。

*connectors*

一个 Boolean，指定是否显示连接器。默认值为 OFF。

*cnxEndPoints*

一个 Boolean，指定是否显示连接器端点。此成员仅在 *connectors*=ON 时适用。默认值为 ON。

*cnxLocalAxes*

一个 Boolean，指定是否显示连接器局部坐标系轴。此成员仅在 *connectors*=ON 时适用。默认值为 ON。

*cnxTypeLabels*

一个 Boolean，指定是否显示连接器截面类型标签。此成员仅在 *connectors*=ON 时适用。默认值为 ON。

*cnxTagDisplay*

一个 Boolean，指定是否在连接器截面类型标签旁显示标签信息。此成员仅在 *connectors*=ON 且 *cnxTypeLabels*=ON 时适用。默认值为 OFF。

*constraints*

一个 Boolean，指定是否显示约束。默认值为 OFF。

*engineeringFeatures*

一个 Boolean，指定是否显示工程特征。默认值为 OFF。

*geometricRestrictions*

一个 Boolean，指定是否显示几何约束。默认值为 OFF。

*renderBeamProfiles*

一个 Boolean，指定是否渲染梁截面。默认值为 OFF。

*beamScaleFactor*

一个 Float，指定梁截面比例因子。beamScaleFactor 必须大于零。默认值为 1.0。

*predefinedFields*

一个 Boolean，指定是否显示场和初始条件。默认值为 OFF。

*interactions*

一个 Boolean，指定是否显示相互作用。默认值为 OFF。

*loads*

一个 Boolean，指定是否显示载荷。默认值为 OFF。

*mesh*

一个 Boolean，指定是否显示网格。默认值为 OFF。

*optimizationTasks*

一个 Boolean，指定是否显示优化任务。默认值为 OFF。

*stopConditions*

一个 Boolean，指定是否显示停止条件。默认值为 OFF。

*renderStyle*

一个 SymbolicConstant，指定视口中图像的渲染方式。可能的值为 WIREFRAME、HIDDEN、SHADED 和 FILLED。默认值为 WIREFRAME。

*bcOptions*

一个 [BCDisplayOptions](pt01ch17pyo02.md) 对象。

*constraintOptions*

一个 [ConstraintDisplayOptions](pt01ch17pyo03.md) 对象。

*displayGroup*

一个 [DisplayGroup](pt01ch16pyo01.md) 对象，指定当前显示组并引用 [Session](pt01ch47pyo01.md) 的 *displayGroups* 成员中的对象。

*displayGroupInstances*

[DisplayGroupInstance](pt01ch16pyo02.md) 对象的存储库。

*engineeringFeatureOptions*

一个 [EngineeringFeatureDisplayOptions](pt01ch17pyo04.md) 对象。

*predefinedFieldOptions*

一个 [PredefinedFieldDisplayOptions](pt01ch17pyo05.md) 对象。

*geometricRestrictionOptions*

一个 [GeometricRestrictionDisplayOptions](pt01ch17pyo07.md) 对象。

*geometryOptions*

一个 [GeometryDisplayOptions](pt01ch17pyo06.md) 对象。

*interactionOptions*

一个 [InteractionDisplayOptions](pt01ch17pyo10.md) 对象。

*loadOptions*

一个 [LoadDisplayOptions](pt01ch17pyo13.md) 对象。

*meshOptions*

一个 [MeshDisplayOptions](pt01ch17pyo14.md) 对象。

*optimizationTaskOptions*

一个 [OptimizationTaskDisplayOptions](pt01ch17pyo15.md) 对象。

*stopConditionOptions*

一个 [StopConditionDisplayOptions](pt01ch17pyo17.md) 对象。

*symbolOptions*

一个 [SymbolDisplayOptions](pt01ch17pyo18.md) 对象。

*visibleInstances*

一个 String 元组，指定在视口中可见的部件实例的名称。默认值为空序列。

*step*

一个 String，指定要显示对象的步骤。可能的值为任何有效的步骤名称。默认值为 "Initial"。





