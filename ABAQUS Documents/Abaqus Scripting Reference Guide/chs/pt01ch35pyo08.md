# 35.8 SymbolOptions 对象

SymbolOptions 对象存储与符号图关联的值和属性。SymbolOptions 对象没有构造函数命令。当您导入 Visualization 模块时，Abaqus 会创建 *defaultOdbDisplay.symbolOptions* 成员。当创建 [OdbDisplay](pt01ch35pyo01.md) 对象时，Abaqus 会创建 *symbolOptions* 成员，使用 *defaultOdbDisplay.symbolOptions* 的值。创建视口时，Abaqus 会创建 *odbDisplay* 成员，使用 *defaultOdbDisplay* 的值。

SymbolOptions 对象通过两种方式之一访问：
- 默认符号选项。创建其他 *symbolOptions* 成员时使用这些设置作为默认值。可以设置这些值以自定义用户首选项。
- 与特定视口关联的符号选项。

SymbolOptions 对象派生自 [DGSymbolOptions](pt01ch40pyo23.md) 对象。

**访问**

```
import visualization
session.defaultOdbDisplay.symbolOptions
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.symbolOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.symbolOptions
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.symbolOptions
session.viewports[*name*].layers[*name*].odbDisplay.symbolOptions
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions.symbolOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.symbolOptions
session.viewports[*name*].odbDisplay.symbolOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions.symbolOptions
```

### 35.8.1 setValues(...)

此方法修改 SymbolOptions 对象。

**必要参数**

无。

**可选参数**

*options*

要从中复制值的 SymbolOptions 对象。如果还向 `setValues` 提供其他参数，它们将覆盖 *options* 中的值。默认值为 `None`。

*vectorQuantity*

一个 SymbolicConstant，指定要显示的向量量。可能的值为 RESULTANT 和 VECTOR_COMPONENT。默认值为 RESULTANT。

*vectorLineThickness*

一个 SymbolicConstant，指定向量线厚度。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*vectorArrowheadStyle*

一个 SymbolicConstant，指定向量箭头样式。可能的值为 NONE、FILLED 和 WIRE。默认值为 WIRE。

*vectorColor*

一个字符串，指定向量颜色。默认值为 "Red"。

*vectorColorMethod*

一个 SymbolicConstant，指定向量颜色方法。可能的值为 UNIFORM 和 SPECTRUM。默认值为 SPECTRUM。

*vectorColorSpectrum*

一个字符串，指定向量颜色光谱名称。默认值为 "Rainbow"。

*vectorIntervalNumber*

一个整数，指定向量符号的颜色间隔数。默认值为 12。

*symbolDensity*

一个 Float，指定随机采样的因子。默认值为 1.0。

*constantLengthArrows*

一个布尔值，指定是否为向量符号使用固定长度箭头。默认值为 OFF。

*tensorColorMethod*

一个 SymbolicConstant，指定张量颜色方法。可能的值为 UNIFORM 和 SPECTRUM。默认值为 SPECTRUM。

*tensorColorSpectrum*

一个字符串，指定张量颜色光谱名称。默认值为 "Rainbow"。

*tensorIntervalNumber*

一个整数，指定张量符号的颜色间隔数。默认值为 12。

*vectorMaxValueAutoCompute*

一个布尔值，指定是否自动计算最大向量值。默认值为 ON。

*vectorMaxValue*

一个 Float，指定用户指定的最大向量值。默认值为 *autoVectorMaxValue*。

*vectorMinValueAutoCompute*

一个布尔值，指定是否自动计算最小向量值。默认值为 ON。

*vectorMinValue*

一个 Float，指定用户指定的最小向量值。默认值为 *autoVectorMinValue*。

*tensorQuantity*

一个 SymbolicConstant，指定要显示的张量。可能的值为 ALL_PRINCIPAL_COMPONENTS、PRINCIPAL_COMPONENT、ALL_DIRECT_COMPONENTS 和 DIRECT_COMPONENT。默认值为 ALL_PRINCIPAL_COMPONENTS。

*arrowSymbolSize*

一个整数，指定向量和张量符号的长度。默认值为 6。

*tensorMaxPrinColor*

一个字符串，指定最大主张量符号的颜色。默认值为 "Red"。

*tensorMinPrinColor*

一个字符串，指定最小主张量符号的颜色。默认值为 "Cyan"。

*tensorMidPrinColor*

一个字符串，指定中间主张量符号的颜色。默认值为 "Yellow"。

*tensorSelectedPrinColor*

一个字符串，指定所选主张量符号的颜色。默认值为 "Red"。

*tensorLineThickness*

一个 SymbolicConstant，指定张量符号的线厚度。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*tensorArrowheadStyle*

一个 SymbolicConstant，指定张量符号的箭头样式。可能的值为 NONE、FILLED 和 WIRE。默认值为 WIRE。

*tensorMaxValueAutoCompute*

一个布尔值，指定是否自动计算最大张量值。默认值为 ON。

*tensorMaxValue*

一个 Float，指定用户指定的最大张量值。默认值为 *autoTensorMaxValue*。

*tensorMinValueAutoCompute*

一个布尔值，指定是否自动计算最小张量值。默认值为 ON。

*tensorMinValue*

一个 Float，指定用户指定的最小张量值。默认值为 *autoTensorMinValue*。

**返回值**

无

**异常**

RangeError。

### 35.8.2 成员

SymbolOptions 对象可以具有以下成员：

*vectorQuantity*

一个 SymbolicConstant，指定要显示的向量量。可能的值为 RESULTANT 和 VECTOR_COMPONENT。默认值为 RESULTANT。

*vectorMaxValueAutoCompute*

一个布尔值，指定是否自动计算最大向量值。默认值为 ON。

*vectorMaxValue*

一个 Float，指定用户指定的最大向量值。默认值为 *autoVectorMaxValue*。

*vectorMinValueAutoCompute*

一个布尔值，指定是否自动计算最小向量值。默认值为 ON。

*vectorMinValue*

一个 Float，指定用户指定的最小向量值。默认值为 *autoVectorMinValue*。

*tensorQuantity*

一个 SymbolicConstant，指定要显示的张量。可能的值为 ALL_PRINCIPAL_COMPONENTS、PRINCIPAL_COMPONENT、ALL_DIRECT_COMPONENTS 和 DIRECT_COMPONENT。默认值为 ALL_PRINCIPAL_COMPONENTS。

*tensorMaxValueAutoCompute*

一个布尔值，指定是否自动计算最大张量值。默认值为 ON。

*tensorMaxValue*

一个 Float，指定用户指定的最大张量值。默认值为 *autoTensorMaxValue*。

*tensorMinValueAutoCompute*

一个布尔值，指定是否自动计算最小张量值。默认值为 ON。

*tensorMinValue*

一个 Float，指定用户指定的最小张量值。默认值为 *autoTensorMinValue*。

*autoVectorMaxValue*

SymbolicConstant NOT_SET 或 Float，指定当 *vectorMaxValueAutoCompute*=ON 时的向量最大值。此值是只读的。默认值为 NOT_SET。

*autoVectorMinValue*

SymbolicConstant NOT_SET 或 Float，指定当 *vectorMinValueAutoCompute*=ON 时的向量最小值。此值是只读的。默认值为 NOT_SET。

*autoTensorMaxValue*

SymbolicConstant NOT_SET 或 Float，指定当 *tensorMaxValueAutoCompute*=ON 时的张量最大值。此值是只读的。默认值为 NOT_SET。

*autoTensorMinValue*

SymbolicConstant NOT_SET 或 Float，指定当 *tensorMinValueAutoCompute*=ON 时的张量最小值。此值是只读的。默认值为 NOT_SET。

*vectorLineThickness*

一个 SymbolicConstant，指定向量线厚度。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*vectorColorMethod*

一个 SymbolicConstant，指定向量颜色方法。可能的值为 UNIFORM 和 SPECTRUM。默认值为 SPECTRUM。

*tensorColorMethod*

一个 SymbolicConstant，指定张量颜色方法。可能的值为 UNIFORM 和 SPECTRUM。默认值为 SPECTRUM。

*vectorArrowheadStyle*

一个 SymbolicConstant，指定向量箭头样式。可能的值为 NONE、FILLED 和 WIRE。默认值为 WIRE。

*arrowSymbolSize*

一个整数，指定向量和张量符号的长度。默认值为 6。

*vectorIntervalNumber*

一个整数，指定向量符号的颜色间隔数。默认值为 12。

*symbolDensity*

一个 Float，指定随机采样的因子。默认值为 1.0。

*constantLengthArrows*

一个布尔值，指定是否为向量符号使用固定长度箭头。默认值为 OFF。

*tensorIntervalNumber*

一个整数，指定张量符号的颜色间隔数。默认值为 12。

*tensorLineThickness*

一个 SymbolicConstant，指定张量符号的线厚度。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 VERY_THIN。

*tensorArrowheadStyle*

一个 SymbolicConstant，指定张量符号的箭头样式。可能的值为 NONE、FILLED 和 WIRE。默认值为 WIRE。

*numberFormatT*

一个 SymbolicConstant，指定张量的数字格式。可能的值为 SCIENTIFIC、FIXED 和 ENGINEERING。默认值为 SCIENTIFIC。

*numberFormatV*

一个 SymbolicConstant，指定向量的数字格式。可能的值为 SCIENTIFIC、FIXED 和 ENGINEERING。默认值为 SCIENTIFIC。

*arrowScaleMode*

一个 SymbolicConstant，指定箭头缩放模式。可能的值为 MODEL_SIZE 和 SCREEN_SIZE。默认值为 MODEL_SIZE。

*drawLabelT*

一个布尔值，指定是否绘制张量标签。默认值为 OFF。

*drawLabelV*

一个布尔值，指定是否绘制向量标签。默认值为 OFF。

*numDigitsT*

一个整数，指定张量标签中的位数。默认值为 2。

*numDigitsV*

一个整数，指定向量标签中的位数。默认值为 2。

*vectorColor*

一个字符串，指定向量颜色。默认值为 "Red"。

*vectorColorSpectrum*

一个字符串，指定向量颜色光谱名称。默认值为 "Rainbow"。

*tensorColorSpectrum*

一个字符串，指定张量颜色光谱名称。默认值为 "Rainbow"。

*textColorT*

一个字符串，指定张量的文本颜色。默认值为 "Yellow"。

*textColorV*

一个字符串，指定向量的文本颜色。默认值为 "Yellow"。

*textFontT*

一个字符串，指定张量的文本字体。默认值为 "verdana"。

*textFontV*

一个字符串，指定向量的文本字体。默认值为 "verdana"。

*tensorMaxPrinColor*

一个字符串，指定最大主张量符号的颜色。默认值为 "Red"。

*tensorMinPrinColor*

一个字符串，指定最小主张量符号的颜色。默认值为 "Cyan"。

*tensorMidPrinColor*

一个字符串，指定中间主张量符号的颜色。默认值为 "Yellow"。

*tensorSelectedPrinColor*

一个字符串，指定所选主张量符号的颜色。默认值为 "Red"。
