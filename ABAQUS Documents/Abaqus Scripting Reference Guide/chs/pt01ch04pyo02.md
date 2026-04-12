# 4.2 AnimationOptions 对象





AnimationOptions 对象用于存储与 [AnimationController](pt01ch04pyo01.md) 对象关联的值和属性。

AnimationOptions 对象没有构造函数命令。创建 [AnimationController](pt01ch04pyo01.md) 对象时，Abaqus 创建 *animationOptions* 成员。

**访问**

```
import animation
session.animationController.animationOptions
```

### 4.2.1 setValues(...)

此方法修改 AnimationOptions 对象。

**必需参数**

无。

**可选参数**

*mode*

一个 SymbolicConstant，指定动画模式。可能的值为 PLAY_ONCE、LOOP、LOOP_BACKWARD 和 SWING。默认值为 LOOP。

*frameRate*

一个 Int，指定动画速率，以帧/秒为单位。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *frameRate* ![](../graphics/ker_eqn00013.gif) 100。默认值为 50。

*frameCounter*

一个 Boolean，指定是否显示帧计数器。默认值为 ON。

*relativeScaling*

一个 SymbolicConstant，指定当 [AnimationController](pt01ch04pyo01.md) 对象的 *animationType*=SCALE_FACTOR 或 HARMONIC 时的相对缩放。可能的值为 FULL_CYCLE 和 HALF_CYCLE。默认值为 HALF_CYCLE。

*numScaleFactorFrames*

一个 Int，指定当 [AnimationController](pt01ch04pyo01.md) 对象的 *animationType*=SCALE_FACTOR 或 HARMONIC 时使用的帧数。默认值为 7。

*timeHistoryMode*

一个 SymbolicConstant，指定时间历史动画是基于时间还是基于帧。可能的值为 FRAME_BASED 和 TIME_BASED。默认值为 FRAME_BASED。

*maxTime*

一个 Float，指定当 *maxTimeAutoCompute* = False 时基于时间的时间历史动画的最大时间。

*maxTimeAutoCompute*

一个 Boolean，指定当 *timeHistoryMode* 设置为 TIME_BASED 时，是否应根据活动帧计算动画最大时间值。默认值为 ON。

*minTime*

一个 Float，指定当 *minTimeAutoCompute* = False 时基于时间的时间历史动画的最小时间。

*minTimeAutoCompute*

一个 Boolean，指定当 *timeHistoryMode* 设置为 TIME_BASED 时，是否应根据活动帧计算动画最小时间值。默认值为 ON。

*timeIncrement*

一个 Float，指定当 *timeHistoryMode* 设置为 TIME_BASED 时选择帧的时间增量。

*xyUseHighlightMethod*

一个 Boolean，指定是否使用高亮方法绘制时间跟踪线和符号。默认值为 ON。

*xyShowLine*

一个 Boolean，指定是否显示时间跟踪线。默认值为 ON。

*xyLineStyle*

一个 SymbolicConstant，指定 *X–Y* 时间跟踪线样式。可能的值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*xyLineThickness*

一个 SymbolicConstant，指定 *X–Y* 时间跟踪线粗细。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 MEDIUM。

*xyLineColor*

一个 String，指定当 *xyUseHighlightMethod* = False 时绘制 *X–Y* 时间跟踪线的颜色。默认值为 "Yellow"。

*xyShowSymbol*

一个 Boolean，指定是否显示时间跟踪符号。默认值为 ON。

*xySymbolMarker*

一个 SymbolicConstant，指定用于所有可动画 *X–Y* 曲线的标记类型，或指定系统将采用与每个曲线关联的标记的 SymbolicConstant DEFAULT。可能的值为：
- FILLED_CIRCLE
- FILLED_SQUARE
- FILLED_DIAMOND
- FILLED_TRI
- HOLLOW_CIRCLE
- HOLLOW_SQUARE
- HOLLOW_DIAMOND
- HOLLOW_TRI
- CROSS
- XMARKER
- DEFAULT

默认值为 DEFAULT。

*xySymbolSize*

一个 SymbolicConstant，指定标记的大小。可能的值为 SMALL、MEDIUM 和 LARGE。默认值为 MEDIUM。

*xySymbolColor*

一个 String，指定当 *xyUseHighlightMethod* = False 时绘制 *X–Y* 时间跟踪符号的颜色。设置为 'Default' 时，系统将采用与每个曲线关联的颜色。默认值为 "Default"。

**返回值**

无

**异常**

无。

### 4.2.2 成员

AnimationOptions 对象可以具有以下成员：

*mode*

一个 SymbolicConstant，指定动画模式。可能的值为 PLAY_ONCE、LOOP、LOOP_BACKWARD 和 SWING。默认值为 LOOP。

*frameRate*

一个 Int，指定动画速率，以帧/秒为单位。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *frameRate* ![](../graphics/ker_eqn00013.gif) 100。默认值为 50。

*frameCounter*

一个 Boolean，指定是否显示帧计数器。默认值为 ON。

*relativeScaling*

一个 SymbolicConstant，指定当 [AnimationController](pt01ch04pyo01.md) 对象的 *animationType*=SCALE_FACTOR 或 HARMONIC 时的相对缩放。可能的值为 FULL_CYCLE 和 HALF_CYCLE。默认值为 HALF_CYCLE。

*numScaleFactorFrames*

一个 Int，指定当 [AnimationController](pt01ch04pyo01.md) 对象的 *animationType*=SCALE_FACTOR 或 HARMONIC 时使用的帧数。默认值为 7。

*timeHistoryMode*

一个 SymbolicConstant，指定时间历史动画是基于时间还是基于帧。可能的值为 FRAME_BASED 和 TIME_BASED。默认值为 FRAME_BASED。

*maxTime*

一个 Float，指定当 *maxTimeAutoCompute* = False 时基于时间的时间历史动画的最大时间。

*maxTimeAutoCompute*

一个 Boolean，指定当 *timeHistoryMode* 设置为 TIME_BASED 时，是否应根据活动帧计算动画最大时间值。默认值为 ON。

*maxTimeAutoValue*

一个 Float，指定当 *timeHistoryMode* 设置为 TIME_BASED 且 *maxTimeAutoCompute* 值为 True 时的最大时间。该值计算为动画处于活动状态的视口中显示的所有活动帧的最大时间。

*minTime*

一个 Float，指定当 *minTimeAutoCompute* = False 时基于时间的时间历史动画的最小时间。

*minTimeAutoCompute*

一个 Boolean，指定当 *timeHistoryMode* 设置为 TIME_BASED 时，是否应根据活动帧计算动画最小时间值。默认值为 ON。

*minTimeAutoValue*

一个 Float，指定当 *timeHistoryMode* 设置为 TIME_BASED 且 *minTimeAutoCompute* 值为 True 时的最小时间。该值计算为动画处于活动状态的视口中显示的所有活动帧的最小时间。

*timeIncrement*

一个 Float，指定当 *timeHistoryMode* 设置为 TIME_BASED 时选择帧的时间增量。

*xyUseHighlightMethod*

一个 Boolean，指定是否使用高亮方法绘制时间跟踪线和符号。默认值为 ON。

*xyShowLine*

一个 Boolean，指定是否显示时间跟踪线。默认值为 ON。

*xyLineStyle*

一个 SymbolicConstant，指定 *X–Y* 时间跟踪线样式。可能的值为 SOLID、DASHED、DOTTED 和 DOT_DASH。默认值为 SOLID。

*xyLineThickness*

一个 SymbolicConstant，指定 *X–Y* 时间跟踪线粗细。可能的值为 VERY_THIN、THIN、MEDIUM 和 THICK。默认值为 MEDIUM。

*xyShowSymbol*

一个 Boolean，指定是否显示时间跟踪符号。默认值为 ON。

*xySymbolMarker*

一个 SymbolicConstant，指定用于所有可动画 *X–Y* 曲线的标记类型，或指定系统将采用与每个曲线关联的标记的 SymbolicConstant DEFAULT。可能的值为：
- FILLED_CIRCLE
- FILLED_SQUARE
- FILLED_DIAMOND
- FILLED_TRI
- HOLLOW_CIRCLE
- HOLLOW_SQUARE
- HOLLOW_DIAMOND
- HOLLOW_TRI
- CROSS
- XMARKER
- DEFAULT

默认值为 DEFAULT。

*xySymbolSize*

一个 SymbolicConstant，指定标记的大小。可能的值为 SMALL、MEDIUM 和 LARGE。默认值为 MEDIUM。

*xyLineColor*

一个 String，指定当 *xyUseHighlightMethod* = False 时绘制 *X–Y* 时间跟踪线的颜色。默认值为 "Yellow"。

*xySymbolColor*

一个 String，指定当 *xyUseHighlightMethod* = False 时绘制 *X–Y* 时间跟踪符号的颜色。设置为 'Default' 时，系统将采用与每个曲线关联的颜色。默认值为 "Default"。




