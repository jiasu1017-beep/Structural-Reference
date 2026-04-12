# 43.5 PsOptions 对象

PsOptions 对象存储 Abaqus 使用 PostScript 格式打印时的设置。PsOptions 对象没有构造函数。启动会话时，Abaqus 会创建 *psOptions* 成员。

**访问**

```
session.psOptions
```

### 43.5.1 setValues(...)

此方法修改 PsOptions 对象。

**必需参数**

无。

**可选参数**

*paperSize*

 SymbolicConstant，指定纸张大小。可选值为：
- LETTER
- LEGAL
- LEDGER
- A0
- A1
- A2
- A3
- A4
- A5

默认值为 LETTER。

*topMargin*

 Float，指定纸的上边距（英寸）。可能的值为 *topMargin* ![](../graphics/ker_eqn00407.gif) 0。默认值为 0.5。

*bottomMargin*

 Float，指定纸的下边距（英寸）。可能的值为 *bottomMargin* ![](../graphics/ker_eqn00407.gif) 0。默认值为 0.5。

*leftMargin*

 Float，指定纸的左边距（英寸）。可能的值为 *leftMargin* ![](../graphics/ker_eqn00407.gif) 0。默认值为 0.5。

*rightMargin*

 Float，指定纸的右边距（英寸）。可能的值为 *rightMargin* ![](../graphics/ker_eqn00407.gif) 0。默认值为 0.5。

*orientation*

 SymbolicConstant，指定图像的方向。可选值为 PORTRAIT 和 LANDSCAPE。默认值为 PORTRAIT。

*logo*

 Boolean，指定输出是否包含 Abaqus 徽标。默认值为 ON。

*date*

 Boolean，指定输出是否包含日期。默认值为 ON。

*resolution*

 SymbolicConstant，指定图像的分辨率（每英寸点数 (dpi)）。只有当 *imageFormat* = VECTOR 时，*resolution* 才能为 DPI_1200。可选值为 DPI_75、DPI_150、DPI_300、DPI_450、DPI_600 和 DPI_1200。默认值为 DPI_150。

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

**注：**宽度和高度的最小值（*minWidth* 和 *minHeight*）为 10 mm（约 0.4 英寸）。

如果 *leftMargin* + *rightMargin* 超出范围：

```
RangeError: leftMargin and rightMargin must produce image width >= minWidth
```

如果 *topMargin* + *bottomMargin* 超出范围：

```
RangeError: topMargin and bottomMargin must produce image height >= minHeight
```

### 43.5.2 成员

PsOptions 对象的成员与 [setValues](pt01ch43pyo05.md#ker-psoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。

