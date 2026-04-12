# 43.6 SvgOptions 对象

SvgOptions 对象存储 Abaqus 以 SVG 格式打印时的设置。SvgOptions 对象没有构造函数。启动会话时，Abaqus 会创建 *svgOptions* 成员。

**访问**

```
session.svgOptions
```

### 43.6.1 setValues(...)

此方法修改 SvgOptions 对象。

**必需参数**

无。

**可选参数**

*imageSize*

 SymbolicConstant SIZE_ON_SCREEN 或一对 Int，指定图像的宽度和高度（以像素为单位）。可能的值为 (*minWidth*, *minHeight* ![](../graphics/ker_eqn00013.gif) *imageSize* ![](../graphics/ker_eqn00013.gif) (*maxWidth* 和 *maxHeight*)。默认值为 SIZE_ON_SCREEN。

**注：**宽度和高度的最小值（*minWidth* 和 *minHeight*）是在当前屏幕分辨率下占据 10 mm 的像素数。该值通常约为 50 像素，宽度和高度可能不同。

宽度和高度的最大值（*maxWidth* 和 *maxHeight*）是系统图形支持的 最大允许像素数，至少与屏幕尺寸一样大。

**返回值**

无

**异常**

RangeError。

如果 *imageSize* 的宽度或高度参数超出范围（其中 *minWidth* 和 *minHeight* 是与给定显示器的约 10 mm 对应的像素数，*maxWidth* 和 *maxHeight* 是系统图形支持的 最大允许像素数）：

```
RangeError: imageSize must be SIZE_ON_SCREEN or a sequence of 2 Ints in the range (minWidth, minHeight) <= (width, height) <= (maxWidth, maxHeight).
```

### 43.6.2 成员

SvgOptions 对象的成员与 [setValues](pt01ch43pyo06.md#ker-svgoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。

