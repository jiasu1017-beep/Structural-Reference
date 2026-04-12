# 40.20 DGOrientationOptions 对象

DGOrientationOptions 对象存储与材料取向图关联的值和属性。DGOrientationOptions 对象没有构造函数命令。创建显示组实例时，Abaqus 使用 *odbDisplay.materialOrientationOptions* 的值创建 *odbDisplayOptions.materialOrientationOptions* 成员。

**访问**

```
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.materialOrientationOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.materialOrientationOptions
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.materialOrientationOptions
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.materialOrientationOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.materialOrientationOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.materialOrientationOptions
```

### 40.20.1 成员

DGOrientationOptions 对象可以具有以下成员：

*showAxis1*

 Boolean，指定是否显示材料取向 triad 的轴 1。默认值为 ON。

*showAxis2*

 Boolean，指定是否显示材料取向 triad 的轴 2。默认值为 ON。

*showAxis3*

 Boolean，指定是否显示材料取向 triad 的轴 3。默认值为 ON。

*symbolSize*

 Float，指定材料取向 triad 的大小。默认值为 6.0。

*lineThickness*

 SymbolicConstant，指定材料取向 triad 的粗细。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*orientation*

 SymbolicConstant，指定用于复合材料的取向。可选值为 PLY 和 LAYUP。默认值为 PLY。

*arrowheadStyle*

 SymbolicConstant，指定材料取向 triad 的箭头样式。可选值为 NONE、FILLED 和 WIRE。默认值为 NONE。

*scaleMode*

 SymbolicConstant，指定材料取向 triad 的缩放基准。可选值为 MODEL_SIZE 和 SCREEN_SIZE。默认值为 MODEL_SIZE。

*axis1Color*

 String，指定材料取向 triad 轴 1 的颜色。默认值为 "Cyan"。

*axis2Color*

 String，指定材料取向 triad 轴 2 的颜色。默认值为 "Yellow"。

*axis3Color*

 String，指定材料取向 triad 轴 3 的颜色。默认值为 "Red"。

