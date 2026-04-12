# 35.6 OrientationOptions 对象

OrientationOptions 对象存储与材料方向图关联的值和属性。OrientationOptions 对象没有构造函数命令。当您导入 Visualization 模块时，Abaqus 会创建 *defaultOdbDisplay.materialOrientationOptions* 成员。当创建 [OdbDisplay](pt01ch35pyo01.md) 对象时，Abaqus 会创建 *materialOrientationOptions* 成员，使用 *defaultOdbDisplay.materialOrientationOptions* 的值。创建视口时，Abaqus 会创建 *odbDisplay* 成员，使用 *defaultOdbDisplay* 的值。

OrientationOptions 对象通过两种方式之一访问：
- 默认材料方向选项。创建其他 *materialOrientationOptions* 成员时使用这些设置作为默认值。可以设置这些值以自定义用户首选项。
- 与特定视口关联的材料方向选项。

OrientationOptions 对象派生自 [DGOrientationOptions](pt01ch40pyo20.md) 对象。

**访问**

```
import visualization
session.defaultOdbDisplay.materialOrientationOptions
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.materialOrientationOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.materialOrientationOptions
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.materialOrientationOptions
session.viewports[*name*].layers[*name*].odbDisplay\
.materialOrientationOptions
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.materialOrientationOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.materialOrientationOptions
session.viewports[*name*].odbDisplay.materialOrientationOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.materialOrientationOptions
```

### 35.6.1 setValues(...)

此方法修改 OrientationOptions 对象。

**必要参数**

无。

**可选参数**

*options*

要从中复制值的 OrientationOptions 对象。如果还向 `setValues` 提供其他参数，它们将覆盖 *options* 中的值。默认值为 `None`。

*axis1Color*

一个字符串，指定材料方向三轴轴 1 的颜色。默认值为 "Cyan"。

*showAxis1*

一个布尔值，指定是否显示材料方向三轴的轴 1。默认值为 ON。

*axis2Color*

一个字符串，指定材料方向三轴轴 2 的颜色。默认值为 "Yellow"。

*showAxis2*

一个布尔值，指定是否显示材料方向三轴的轴 2。默认值为 ON。

*axis3Color*

一个字符串，指定材料方向三轴轴 3 的颜色。默认值为 "Red"。

*showAxis3*

一个布尔值，指定是否显示材料方向三轴的轴 3。默认值为 ON。

*symbolSize*

一个 Float，指定材料方向三轴的大小。默认值为 6.0。

*lineThickness*

一个 SymbolicConstant，指定材料方向三轴的厚度。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*orientation*

一个 SymbolicConstant，指定用于复合材料的取向。可能的值为 PLY 和 LAYUP。默认值为 PLY。

*arrowheadStyle*

一个 SymbolicConstant，指定材料方向三轴的箭头样式。可能的值为 NONE、FILLED 和 WIRE。默认值为 NONE。

*scaleMode*

一个 SymbolicConstant，指定材料方向三轴的缩放基准。可能的值为 MODEL_SIZE 和 SCREEN_SIZE。默认值为 MODEL_SIZE。

**返回值**

无

**异常**

RangeError。

### 35.6.2 成员

OrientationOptions 对象可以具有以下成员：

*showAxis1*

一个布尔值，指定是否显示材料方向三轴的轴 1。默认值为 ON。

*showAxis2*

一个布尔值，指定是否显示材料方向三轴的轴 2。默认值为 ON。

*showAxis3*

一个布尔值，指定是否显示材料方向三轴的轴 3。默认值为 ON。

*symbolSize*

一个 Float，指定材料方向三轴的大小。默认值为 6.0。

*lineThickness*

一个 SymbolicConstant，指定材料方向三轴的厚度。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*orientation*

一个 SymbolicConstant，指定用于复合材料的取向。可能的值为 PLY 和 LAYUP。默认值为 PLY。

*arrowheadStyle*

一个 SymbolicConstant，指定材料方向三轴的箭头样式。可能的值为 NONE、FILLED 和 WIRE。默认值为 NONE。

*scaleMode*

一个 SymbolicConstant，指定材料方向三轴的缩放基准。可能的值为 MODEL_SIZE 和 SCREEN_SIZE。默认值为 MODEL_SIZE。

*axis1Color*

一个字符串，指定材料方向三轴轴 1 的颜色。默认值为 "Cyan"。

*axis2Color*

一个字符串，指定材料方向三轴轴 2 的颜色。默认值为 "Yellow"。

*axis3Color*

一个字符串，指定材料方向三轴轴 3 的颜色。默认值为 "Red"。
