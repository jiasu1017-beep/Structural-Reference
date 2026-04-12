# 40.6 FreeBodyOptions 对象

FreeBodyOptions 对象存储与自由体图关联的值和属性。FreeBodyOptions 对象没有构造函数命令。导入 Visualization 模块时，Abaqus 创建 *defaultOdbDisplay.freeBodyOptions* 成员。当 Abaqus 创建 [OdbDisplay](pt01ch35pyo01.md) 对象时，会使用 *defaultOdbDisplay.freeBodyOptions* 的值创建 *FreeBodyOptions* 成员。创建视口时，Abaqus 使用 *defaultOdbDisplay* 的值创建 *odbDisplay* 成员。

FreeBodyOptions 对象通过以下两种方式之一访问：
- 默认自由体选项。创建其他 *freeBodyOptions* 成员时使用这些设置作为默认值。可以设置这些设置来自定义用户首选项。
- 与特定视口关联的自由体选项。

**访问**

```
import visualization
session.defaultOdbDisplay.freeBodyOptions
session.viewports[*name*].layers[*name*].odbDisplay.freeBodyOptions
session.viewports[*name*].odbDisplay.freeBodyOptions
```

### 40.6.1 setValues(...)

此方法修改 FreeBodyOptions 对象。

**必需参数**

无。

**可选参数**

*comp1ColorF*

 String，指定第一个分力的颜色。默认值为 "#FF1932"。

*comp1ColorM*

 String，指定第一个分力的颜色。默认值为 "#FF1932"。

*comp2ColorF*

 String，指定第二个分力的颜色。默认值为 "#FF1932"。

*comp2ColorM*

 String，指定第二个分力的颜色。默认值为 "#FF1932"。

*comp3ColorF*

 String，指定第三个分力的颜色。默认值为 "#FF1932"。

*comp3ColorM*

 String，指定第三个分力的颜色。默认值为 "#FF1932"。

*resultantColorF*

 String，指定合力的颜色。默认值为 "#FF1932"。

*resultantColorM*

 String，指定合力矩的颜色。默认值为 "#FF1932"。

*textColorF*

 String，指定力的文字颜色。默认值为 "Yellow"。

*textColorM*

 String，指定力矩的文字颜色。默认值为 "Yellow"。

*textFontF*

 String，指定力的文字字体。默认值为 "verdana"。

*textFontM*

 String，指定力矩的文字字体。默认值为 "verdana"。

*numberFormatF*

 SymbolicConstant，指定力的数字格式。可选值为 SCIENTIFIC、FIXED 和 ENGINEERING。默认值为 SCIENTIFIC。

*numberFormatM*

 SymbolicConstant，指定力矩的数字格式。可选值为 SCIENTIFIC、FIXED 和 ENGINEERING。默认值为 SCIENTIFIC。

*scaleModeF*

 SymbolicConstant，指定力的尺寸缩放模式。可选值为 MODEL_SIZE 和 SCREEN_SIZE。默认值为 MODEL_SIZE。

*scaleModeM*

 SymbolicConstant，指定力矩的尺寸缩放模式。可选值为 MODEL_SIZE 和 SCREEN_SIZE。默认值为 MODEL_SIZE。

*vectorDisplay*

 SymbolicConstant，指定矢量显示模式。可选值为 RESULTANT 和 COMPONENT。默认值为 RESULTANT。

*numDigitsF*

 Int，指定力标签中的数字位数。默认值为 3。

*numDigitsM*

 Int，指定力矩标签中的数字位数。默认值为 3。

*sizePercentageF*

 Float，指定力符号作为屏幕或模型百分比的大小。默认值为 10.0。

*sizePercentageM*

 Float，指定力矩符号作为屏幕或模型百分比的大小。默认值为 10.0。

*thresholdF*

 Float，指定力的阈值。默认值为 10–6。

*thresholdM*

 Float，指定力矩的阈值。默认值为 10–6。

*drawLabelF*

 Boolean，指定是否绘制力标签。默认值为 ON。

*drawLabelM*

 Boolean，指定是否绘制力矩标签。默认值为 ON。

*showComp1F*

 Boolean，指定是否显示第一个分力。默认值为 ON。

*showComp1M*

 Boolean，指定是否显示第一个分力矩。默认值为 ON。

*showComp2F*

 Boolean，指定是否显示第二个分力。默认值为 ON。

*showComp2M*

 Boolean，指定是否显示第二个分力矩。默认值为 ON。

*showComp3F*

 Boolean，指定是否显示第三个分力。默认值为 ON。

*showComp3M*

 Boolean，指定是否显示第三个分力矩。默认值为 ON。

*showForce*

 Boolean，指定是否显示力。默认值为 ON。

*showMoment*

 Boolean，指定是否显示力矩。默认值为 ON。

*constantLengthArrow*

 Boolean，指定是否为所有箭头使用恒定长度。默认值为 OFF。

**返回值**

无

**异常**

无。

### 40.6.2 成员

FreeBodyOptions 对象的成员与 [setValues](pt01ch40pyo06.md#ker-freebodyoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。

