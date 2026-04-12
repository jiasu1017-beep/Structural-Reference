# 4.4 ImageAnimationOptions 对象





ImageAnimationOptions 对象用于存储与保存视口动画相关的值和属性。ImageAnimationOptions 对象没有构造函数。导入动画模块时，Abaqus 创建 *imageAnimationOptions* 成员。

**访问**

```
import animation
session.imageAnimationOptions
```

### 4.4.1 setValues(...)

此方法修改 ImageAnimationOptions 对象。

**必需参数**

无。

**可选参数**

*frameRate*

一个 Int，指定要记录在保存的动画文件上的帧速率。以每秒帧数计的有效帧速率将通过时间比例除以给定的帧速率获得。

*timeScale*

一个 Int，指定要应用于帧速率的时间比例。

*vpDecorations*

一个 Boolean，指定是否捕获视口边框和标题。默认值为 ON。

*vpBackground*

一个 Boolean，指定是否捕获视口背景。默认值为 OFF。

*compass*

一个 Boolean，指定是否捕获视口罗盘。默认值为 OFF。

**返回值**

无

**异常**

无。

### 4.4.2 成员

ImageAnimationOptions 对象具有与 [setValues](pt01ch04pyo04.md#ker-imageanimationoptions-setvalues-pyc) 方法参数相同名称和描述的成员。




