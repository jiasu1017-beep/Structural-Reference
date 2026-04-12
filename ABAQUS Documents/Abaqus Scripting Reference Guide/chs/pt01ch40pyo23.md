# 40.23 DGSymbolOptions 对象

DGSymbolOptions 对象存储与符号图关联的值和属性。DGSymbolOptions 对象没有构造函数命令。创建显示组实例时，Abaqus 使用 *odbDisplay.symbolOptions* 的值创建 *odbDisplayOptions.symbolOptions* 成员。

**访问**

```
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.symbolOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.symbolOptions
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.symbolOptions
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.symbolOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.symbolOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.symbolOptions
```

### 40.23.1 成员

DGSymbolOptions 对象可以具有以下成员：

*vectorLineThickness*

 SymbolicConstant，指定矢量线宽。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*vectorColorMethod*

 SymbolicConstant，指定矢量颜色方法。可选值为 UNIFORM 和 SPECTRUM。默认值为 SPECTRUM。

*tensorColorMethod*

 SymbolicConstant，指定张量颜色方法。可选值为 UNIFORM 和 SPECTRUM。默认值为 SPECTRUM。

*vectorArrowheadStyle*

 SymbolicConstant，指定矢量箭头样式。可选值为 NONE、FILLED 和 WIRE。默认值为 WIRE。

*arrowSymbolSize*

 Int，指定矢量和张量符号的长度。默认值为 6。

*vectorIntervalNumber*

 Int，指定矢量符号的颜色间隔数。默认值为 12。

*symbolDensity*

 Float，指定随机采样的因子。默认值为 1.0。

*constantLengthArrows*

 Boolean，指定是否为矢量符号使用恒定长度箭头。默认值为 OFF。

*tensorIntervalNumber*

 Int，指定张量符号的颜色间隔数。默认值为 12。

*tensorLineThickness*

 SymbolicConstant，指定张量符号的线宽。可选值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*tensorArrowheadStyle*

 SymbolicConstant，指定张量符号的箭头样式。可选值为 NONE、FILLED 和 WIRE。默认值为 WIRE。

*numberFormatT*

 SymbolicConstant，指定张量的数字格式。可选值为 SCIENTIFIC、FIXED 和 ENGINEERING。默认值为 SCIENTIFIC。

*numberFormatV*

 SymbolicConstant，指定矢量的数字格式。可选值为 SCIENTIFIC、FIXED 和 ENGINEERING。默认值为 SCIENTIFIC。

*arrowScaleMode*

 SymbolicConstant，指定箭头缩放模式。可选值为 MODEL_SIZE 和 SCREEN_SIZE。默认值为 MODEL_SIZE。

*drawLabelT*

 Boolean，指定是否绘制张量标签。默认值为 OFF。

*drawLabelV*

 Boolean，指定是否绘制矢量标签。默认值为 OFF。

*numDigitsT*

 Int，指定张量标签中的数字位数。默认值为 2。

*numDigitsV*

 Int，指定矢量标签中的数字位数。默认值为 2。

*vectorColor*

 String，指定矢量颜色。默认值为 "Red"。

*vectorColorSpectrum*

 String，指定矢量颜色光谱名称。默认值为 "Rainbow"。

*tensorColorSpectrum*

 String，指定张量颜色光谱名称。默认值为 "Rainbow"。

*textColorT*

 String，指定张量的文字颜色。默认值为 "Yellow"。

*textColorV*

 String，指定矢量的文字颜色。默认值为 "Yellow"。

*textFontT*

 String，指定张量的文字字体。默认值为 "verdana"。

*textFontV*

 String，指定矢量的文字字体。默认值为 "verdana"。

*tensorMaxPrinColor*

 String，指定最大主张量符号的颜色。默认值为 "Red"。

*tensorMinPrinColor*

 String，指定最小主张量符号的颜色。默认值为 "Cyan"。

*tensorMidPrinColor*

 String，指定中间主张量符号的颜色。默认值为 "Yellow"。

*tensorSelectedPrinColor*

 String，指定所选主张量符号的颜色。默认值为 "Red"。

