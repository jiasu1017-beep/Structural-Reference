# 43.2 EpsOptions 对象

EpsOptions 对象存储 Abaqus 使用 Encapsulated PostScript 格式打印时的设置。EpsOptions 对象没有构造函数。启动会话时，Abaqus 会创建 *epsOptions* 成员。

**访问**

```
session.epsOptions
```

### 43.2.1 setValues(...)

此方法修改 EpsOptions 对象。

**必需参数**

无。

**可选参数**

*imageSize*

 SymbolicConstant SIZE_ON_SCREEN 或一对 Float，指定图像在 *units* 指定的单位下的宽度和高度。可能的数值是 *imageSize* ![](../graphics/ker_eqn00407.gif) (*minWidth*, *minHeight*)。默认值为 SIZE_ON_SCREEN。

**注：**宽度和高度的最小值（*minWidth* 和 *minHeight*）为 10 mm（约 0.4 英寸）。

*units*

 SymbolicConstant，指定 *imageSize* 参数的单位。如果 *imageSize* 是 SIZE_ON_SCREEN，则忽略此参数。可选值为 INCHES 和 MM。默认值为 INCHES。

*resolution*

 SymbolicConstant，指定图像的分辨率（每英寸点数 (dpi)）。只有当 *imageFormat*=VECTOR 时，*resolution* 才能为 DPI_1200。可选值为 DPI_75、DPI_150、DPI_300、DPI_450、DPI_600 和 DPI_1200。默认值为 DPI_150。

*fontType*

 SymbolicConstant，指定要应用的 PostScript 字体替换规则。可选值为 PS_ALWAYS、PS_IF_AVAILABLE 和 AS_DISPLAYED。默认值为 PS_IF_AVAILABLE。

*imageFormat*

 SymbolicConstant，指定视口显示的表示方式。可选值为 VECTOR 和 RASTER。默认值为 VECTOR。

*shadingQuality*

 SymbolicConstant，指定矢量图像中曲面的着色细度。可选值为 EXTRA COARSE、COARSE、MEDIUM、FINE 和 EXTRA FINE。默认值为 MEDIUM。

**返回值**

无

**异常**

RangeError。

如果 *imageSize* 的任一元素超出范围：

```
RangeError: imageSize must be SIZE_ON_SCREEN or a sequence of 2 Floats >= (*minWidth*, *minHeight*)
```

### 43.2.2 成员

EpsOptions 对象的成员与 [setValues](pt01ch43pyo02.md#ker-epsoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。

