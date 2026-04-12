# 5.2 AnnotationsToPlotArray 对象





AnnotationsToPlotArray 对象是一个序列，存储已绘制注释的引用。通过向此序列添加注释和从中移除注释，您可以控制要在特定视口中显示的注释。

**访问**

```
import annotationToolset
session.viewports[*name*].annotationsToPlot
```

### 5.2.1 bringForward(...)

此方法将 [Annotation](pt01ch05pyo01.md) 对象在 AnnotationsToPlotArray 序列中向前移动一个位置。

**必需参数**

*index*

一个 Int，指定 [Annotation](pt01ch05pyo01.md) 对象在 AnnotationsToPlotArray 序列中的索引。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 5.2.2 bringToFront(...)

此方法将 [Annotation](pt01ch05pyo01.md) 对象带到 AnnotationsToPlotArray 序列的开头。

**必需参数**

*index*

一个 Int，指定 [Annotation](pt01ch05pyo01.md) 对象在 AnnotationsToPlotArray 序列中的索引。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 5.2.3 moveAfter(...)

此方法将 [Annotation](pt01ch05pyo01.md) 对象移动到同一 AnnotationsToPlotArray 序列中另一个对象之后。

**必需参数**

*index*

一个 Integer，指定 [Annotation](pt01ch05pyo01.md) 对象在 AnnotationsToPlotArray 序列中的索引。

*other*

一个 Integer，指定 [Annotation](pt01ch05pyo01.md) 对象在 AnnotationsToPlotArray 序列中的索引，此对象将被移动到此对象之后。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 5.2.4 moveBefore(...)

此方法将 [Annotation](pt01ch05pyo01.md) 对象移动到同一 AnnotationsToPlotArray 序列中另一个对象之前。

**必需参数**

*index*

一个 Int，指定 [Annotation](pt01ch05pyo01.md) 对象在 AnnotationsToPlotArray 序列中的索引。

*other*

一个 Int，指定 [Annotation](pt01ch05pyo01.md) 对象在 AnnotationsToPlotArray 序列中的索引，此对象将被移动到此对象之前。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 5.2.5 sendBackward(...)

此方法将 [Annotation](pt01ch05pyo01.md) 对象在 AnnotationsToPlotArray 序列中向后移动一个位置。

**必需参数**

*index*

一个 Int，指定 [Annotation](pt01ch05pyo01.md) 对象在 AnnotationsToPlotArray 序列中的索引。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 5.2.6 sendToBack(...)

此方法将 [Annotation](pt01ch05pyo01.md) 对象发送到 AnnotationsToPlotArray 序列的末尾。

**必需参数**

*index*

一个 Int，指定 [Annotation](pt01ch05pyo01.md) 对象在 AnnotationsToPlotArray 序列中的索引。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 5.2.7 成员

AnnotationsToPlotArray 对象没有成员。




