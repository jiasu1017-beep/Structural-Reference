# 17.16 PartDisplayOptions 对象









PartDisplayOptions 对象存储指定如何在特定视口中显示部件的设置。PartDisplayOptions 对象没有构造函数。创建新视口时，设置从当前视口复制。

**访问**

```
session.viewports[*name*].layers[*name*].partDisplay
import part
session.viewports[*name*].partDisplay
```

### 17.16.1 setValues(...)

此方法修改 PartDisplayOptions 对象。

**必需参数**

无。

**可选参数**

*renderStyle*

一个 SymbolicConstant，指定视口中图像的渲染方式。可能的值为 WIREFRAME、HIDDEN 和 SHADED。默认值为 WIREFRAME。

*visibleDisplayGroups*

一个 [DisplayGroup](pt01ch16pyo01.md) 对象序列，指定在视口中可见的 DisplayGroups。当前该序列最多可包含一个 [DisplayGroup](pt01ch16pyo01.md) 对象。默认值为空序列。

*engineeringFeatures*

一个 Boolean，指定是否显示工程特征。默认值为 OFF。

*renderBeamProfiles*

一个 Boolean，指定是否渲染梁截面。默认值为 OFF。

*beamScaleFactor*

一个 Float，指定梁截面比例因子。beamScaleFactor 必须大于零。默认值为 1.0。

**返回值**

无

**异常**

RangeError。

### 17.16.2 成员

PartDisplayOptions 对象可具有以下成员：

*engineeringFeatures*

一个 Boolean，指定是否显示工程特征。默认值为 OFF。

*renderBeamProfiles*

一个 Boolean，指定是否渲染梁截面。默认值为 OFF。

*beamScaleFactor*

一个 Float，指定梁截面比例因子。beamScaleFactor 必须大于零。默认值为 1.0。

*mesh*

一个 Boolean，指定是否显示网格。

*renderStyle*

一个 SymbolicConstant，指定视口中图像的渲染方式。可能的值为 WIREFRAME、HIDDEN 和 SHADED。默认值为 WIREFRAME。

*displayGroup*

一个 [DisplayGroup](pt01ch16pyo01.md) 对象，指定当前显示组并引用 [Session](pt01ch47pyo01.md) 的 *displayGroups* 成员中的对象。

*displayGroupInstances*

[DisplayGroupInstance](pt01ch16pyo02.md) 对象的存储库。

*engineeringFeatureOptions*

一个 [EngineeringFeatureDisplayOptions](pt01ch17pyo04.md) 对象。

*geometryOptions*

一个 [GeometryDisplayOptions](pt01ch17pyo06.md) 对象。

*meshOptions*

一个 [MeshDisplayOptions](pt01ch17pyo14.md) 对象。





