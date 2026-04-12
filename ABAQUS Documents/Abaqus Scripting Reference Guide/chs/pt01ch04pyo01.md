# 4.1 AnimationController 对象





AnimationController 对象控制要在视口中显示的所有基于对象的动画。AnimationController 对象没有构造函数。当创建 [Session](pt01ch47pyo01.md) 对象时，Abaus 创建 *animationController* 成员。

**访问**

```
import animation
session.animationController
```

### 4.1.1 play(...)

此方法开始动画。

**必需参数**

无。

**可选参数**

*duration*

SymbolicConstant UNLIMITED 或一个 Int，指定播放动画的秒数。默认值为 UNLIMITED。

**返回值**

无

**异常**

如果 *animationType*=NONE：

```
AnimationError: animationType not set
```

### 4.1.2 stop()

此方法停止动画。

**参数**

无。

**返回值**

无

**异常**

无。

### 4.1.3 incrementFrame()

此方法增加动画帧。

**参数**

无。

**返回值**

无

**异常**

无。

### 4.1.4 decrementFrame()

此方法减少动画帧。

**参数**

无。

**返回值**

无

**异常**

无。

### 4.1.5 showFrame(...)

此方法渲染动画的指定帧。

**必需参数**

无。

**可选参数**

*frame*

一个 Int，指定帧号。

*value*

一个 Float，对于 *animationType*=TIME_HISTORY 指定最近到此值的时间的帧，对于 *animationType*=HARMONIC 指定最近到此值角度的帧，对于 *animationType*=SCALE_FACTOR 指定最近到此值的比例值的帧。

**返回值**

无

**异常**

无。

### 4.1.6 showFirstFrame()

此方法渲染动画的第一帧。

**参数**

无。

**返回值**

无

**异常**

无。

### 4.1.7 showLastFrame()

此方法渲染动画的最后一帧。

**参数**

无。

**返回值**

无

**异常**

无。

### 4.1.8 setValues(...)

此方法修改 AnimationController 对象。

**必需参数**

无。

**可选参数**

*animationType*

一个 SymbolicConstant，指定要播放的电影类型。可能的值为 SCALE_FACTOR、HARMONIC、TIME_HISTORY 和 NONE。默认值为 NONE。

*viewports*

一个 String 对序列，指定动画处于活动状态的视口名称，后跟图层名称，或 SymbolicConstant ALL。如果未提供图层名称，则使用当前图层。如果视口处于单显示模式，则如果指定了图层名称则忽略图层名称。默认值为空序列。

**返回值**

无

**异常**

RangeError。

### 4.1.9 成员

AnimationController 对象可以具有以下成员：

*animationType*

一个 SymbolicConstant，指定要播放的电影类型。可能的值为 SCALE_FACTOR、HARMONIC、TIME_HISTORY 和 NONE。默认值为 NONE。

*state*

一个 SymbolicConstant，指定动画控制器的状态。可能的值为 STOP 和 PLAY。默认值为 STOP。

*animationOptions*

一个 [AnimationOptions](pt01ch04pyo02.md) 对象。

*viewports*

一个 String 对元组，指定动画处于活动状态的视口名称，后跟图层名称，或 SymbolicConstant ALL。如果未提供图层名称，则使用当前图层。如果视口处于单显示模式，则如果指定了图层名称则忽略图层名称。默认值为空序列。




