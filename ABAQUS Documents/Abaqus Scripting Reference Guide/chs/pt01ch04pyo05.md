# 4.5 ImageAnimation 对象





ImageAnimation 对象用于逐帧构建动画。

**访问**

```
import animation
session.imageAnimation
```

### 4.5.1 ImageAnimation(...)

此方法从指定的文件名和格式创建 ImageAnimation 对象。

**路径**

```
session.ImageAnimation
```

**必需参数**

*fileName*

一个 String，指定要生成的动画文件的名称。

*format*

一个 SymbolicConstant，指定生成文件的格式。可能的值为 AVI、QUICKTIME。

**可选参数**

无。

**返回值**

一个 ImageAnimation 对象。

**异常**

无。

### 4.5.2 writeFrame(...)

此方法向 ImageAnimation 对象添加一帧。

**必需参数**

无。

**可选参数**

*canvasObjects*

一个序列，指定要捕获的画布对象。默认是捕获所有画布对象。

**返回值**

无

**异常**

无。

### 4.5.3 close()

此方法关闭 ImageAnimation 对象。

**参数**

无。

**返回值**

无

**异常**

无。

### 4.5.4 closed()

此方法指示 ImageAnimation 是打开还是关闭以写入动画帧。

**参数**

无。

**返回值**

无

**异常**

无。

### 4.5.5 成员

ImageAnimation 对象具有以下成员：

*fileName*

一个 String，指定要将动画帧写入的文件。




