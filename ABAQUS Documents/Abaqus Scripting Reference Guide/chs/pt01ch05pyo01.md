# 5.1 Annotation 对象





Annotation 对象是其他 Annotation 对象的抽象基类型。Annotation 对象没有显式构造函数。Annotation 对象的方法和成员对从 Annotation 派生的所有对象都是通用的。

**访问**

```
import annotationToolset
mdb.annotations[*name*]
session.odbs[*name*].userData.annotations[*name*]
session.viewports[*name*].annotationsToPlot[*i*]
```

### 5.1.1 bringToFront()

此方法将 Annotation 对象带到注释栈的顶部。

**参数**

无。

**返回值**

无

**异常**

无。

### 5.1.2 sendToBack()

此方法将 Annotation 对象发送到注释栈的底部。

**参数**

无。

**返回值**

无

**异常**

无。

### 5.1.3 bringForward()

此方法将 Annotation 对象在注释栈中向上移动一个位置。

**参数**

无。

**返回值**

无

**异常**

无。

### 5.1.4 sendBackward()

此方法将 Annotation 对象在注释栈中向下移动一个位置。

**参数**

无。

**返回值**

无

**异常**

无。

### 5.1.5 moveBefore(...)

此方法将 Annotation 对象移动到同一仓库中另一个对象之前。

**必需参数**

*name*

一个 String，指定另一个 Annotation 对象的名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 5.1.6 moveAfter(...)

此方法将 Annotation 对象移动到同一仓库中另一个对象之后。

**必需参数**

*name*

一个 String，指定另一个 Annotation 对象的名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 5.1.7 translate(...)

此方法在视口平面上平移 Annotation 对象。

**必需参数**

无。

**可选参数**

*x*

一个 Float，指定 *X* 方向以毫米为单位的平移量。

*y*

一个 Float，指定 *Y* 方向以毫米为单位的平移量。

**返回值**

无

**异常**

无。

### 5.1.8 成员

Annotation 对象具有以下成员：

*name*

一个 String，指定注释仓库键。




