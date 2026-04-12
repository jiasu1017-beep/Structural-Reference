# 40.24 ViewCutOptions 对象

ViewCutOptions 对象存储与视图切割图关联的值和属性。ViewCutOptions 对象没有构造函数命令。导入 Visualization 模块时，Abaqus 创建 *defaultOdbDisplay.viewCutOptions* 成员。当 Abaqus 创建 [OdbDisplay](pt01ch35pyo01.md) 对象时，会使用 *defaultOdbDisplay.viewCutOptions* 的值创建 *viewCutOptions* 成员。创建视口时，Abaqus 使用 *defaultOdbDisplay* 的值创建 *odbDisplay* 成员。

ViewCutOptions 对象通过以下两种方式之一访问：
- 默认视图切割选项。创建其他 *viewCutOptions* 成员时使用这些设置作为默认值。可以设置这些设置来自定义用户首选项。
- 与特定视口关联的视图切割选项。

**访问**

```
import visualization
session.defaultOdbDisplay.viewCutOptions
session.viewports[*name*].layers[*name*].odbDisplay.viewCutOptions
session.viewports[*name*].odbDisplay.viewCutOptions
```

### 40.24.1 setValues(...)

此方法修改 ViewCutOptions 对象。

**必需参数**

无。

**可选参数**

*options*

 ViewCutOptions 对象，指定要复制的值。如果还有其他参数提供给 `setValues`，它们将覆盖 *options* 中的值。默认值为 `None`。

*belowOptions*

 `None` 或 [OptionArg](pt01ch40pyo19.md) 对象，指定用于定义切割下方模型选项的值。默认值为 `None`。

*useBelowOptions*

 Boolean，指定是否使用为切割下方显示定义的选项。默认值为 OFF。

*onOptions*

 `None` 或 [OptionArg](pt01ch40pyo19.md) 对象，指定用于定义切割上模型选项的值。默认值为 `None`。

*useOnOptions*

 Boolean，指定是否使用为切割上显示定义的选项。默认值为 OFF。

*aboveOptions*

 `None` 或 [OptionArg](pt01ch40pyo19.md) 对象，指定用于定义切割上方模型选项的值。默认值为 `None`。

*useAboveOptions*

 Boolean，指定是否使用为切割上方显示定义的选项。默认值为 OFF。

*freeBodyCutThru*

 SymbolicConstant，指定自由体切割的域。可选值为 CURRENT_DISPLAY_GROUP 和 WHOLE_MODEL。默认值为 CURRENT_DISPLAY_GROUP。

*freeBodyStepThru*

 SymbolicConstant，指定自由体步进的域。可选值为 ACTIVE_CUT_RANGE 和 PREDEFINED_PATH。默认值为 ACTIVE_CUT_RANGE。

*numCutFreeBody*

 Int，指定每个视图切割的自由体数目。默认值为 1。

*displaySlicing*

 Boolean，指定是否显示切片。默认值为 OFF。

*slicingAtPathNodes*

 Boolean，指定是否在路径节点处切片。默认值为 OFF。

*freeBodySumOnPath*

 Boolean，指定是否将求和点放在路径上。默认值为 ON。

*cutFreeBodyMin*

 Float，指定自由体最小值。默认值为 0.0。

*cutFreeBodyMax*

 Float，指定自由体最大值。默认值为 0.0。

*showHeatFlowRate*

 SymbolicConstant，指定是否在可用时显示热流率。可选值为 ON 和 OFF。默认值为 ON。

*summationLoc*

 SymbolicConstant，指定自由体切割的求和位置。可选值为 CENTROID 和 SPECIFY。默认值为 CENTROID。

*componentResolution*

 SymbolicConstant，指定自由体切割的分量分辨率选择。可选值为 NORMAL_TANGENTIAL 和 CSYS。默认值为 NORMAL_TANGENTIAL。

*csysName*

 SymbolicConstant GLOBAL 或 String，指定自由体切割分量分辨率的坐标系名称。默认值为 GLOBAL。

*pathName*

 String，指定切片发生所沿路径的名称。默认值为空字符串。

*summationPoint*

三个 Float 的序列，指定自由体切割的求和点。默认值为 (0, 0, 0)。

*yAxis*

三个 Float 的序列，指定自由体分量分辨率的 Y 轴。默认值为 (0, 1, 0)。

**返回值**

无

**异常**

RangeError。

### 40.24.2 成员

ViewCutOptions 对象可以具有以下成员：

*useBelowOptions*

 Boolean，指定是否使用为切割下方显示定义的选项。默认值为 OFF。

*useOnOptions*

 Boolean，指定是否使用为切割上显示定义的选项。默认值为 OFF。

*useAboveOptions*

 Boolean，指定是否使用为切割上方显示定义的选项。默认值为 OFF。

*numCutFreeBody*

 Int，指定每个视图切割的自由体数目。默认值为 1。

*displaySlicing*

 Boolean，指定是否显示切片。默认值为 OFF。

*slicingAtPathNodes*

 Boolean，指定是否在路径节点处切片。默认值为 OFF。

*freeBodySumOnPath*

 Boolean，指定是否将求和点放在路径上。默认值为 ON。

*cutFreeBodyMin*

 Float，指定自由体最小值。默认值为 0.0。

*cutFreeBodyMax*

 Float，指定自由体最大值。默认值为 0.0。

*freeBodyCutThru*

 SymbolicConstant，指定自由体切割的域。可选值为 CURRENT_DISPLAY_GROUP 和 WHOLE_MODEL。默认值为 CURRENT_DISPLAY_GROUP。

*freeBodyStepThru*

 SymbolicConstant，指定自由体步进的域。可选值为 ACTIVE_CUT_RANGE 和 PREDEFINED_PATH。默认值为 ACTIVE_CUT_RANGE。

*showHeatFlowRate*

 SymbolicConstant，指定是否在可用时显示热流率。可选值为 ON 和 OFF。默认值为 ON。

*summationLoc*

 SymbolicConstant，指定自由体切割的求和位置。可选值为 CENTROID 和 SPECIFY。默认值为 CENTROID。

*componentResolution*

 SymbolicConstant，指定自由体切割的分量分辨率选择。可选值为 NORMAL_TANGENTIAL 和 CSYS。默认值为 NORMAL_TANGENTIAL。

*belowOptions*

 `None` 或 [OptionArg](pt01ch40pyo19.md) 对象，指定用于定义切割下方模型选项的值。默认值为 `None`。

*onOptions*

 `None` 或 [OptionArg](pt01ch40pyo19.md) 对象，指定用于定义切割上模型选项的值。默认值为 `None`。

*aboveOptions*

 `None` 或 [OptionArg](pt01ch40pyo19.md) 对象，指定用于定义切割上方模型选项的值。默认值为 `None`。

*csysName*

 SymbolicConstant GLOBAL 或 String，指定自由体切割分量分辨率的坐标系名称。默认值为 GLOBAL。

*pathName*

 String，指定切片发生所沿路径的名称。默认值为空字符串。

*summationPoint*

三个 Float 的元组，指定自由体切割的求和点。默认值为 (0, 0, 0)。

*yAxis*

三个 Float 的元组，指定自由体分量分辨率的 Y 轴。默认值为 (0, 1, 0)。

