# 43.3 PageSetupOptions 对象

PageSetupOptions 对象存储 Abaqus 使用 Windows 打印机打印时的设置。PageSetupOptions 对象没有构造函数。启动会话时，Abaqus 会创建 *pageSetupOptions* 成员。

**访问**

```
session.pageSetupOptions
```

### 43.3.1 setValues(...)

此方法修改 PageSetupOptions 对象。

**必需参数**

无。

**可选参数**

*imageSize*

 SymbolicConstant 或一对 Float，指定以当前选择的单位（英寸或毫米）打印图像的大小。可选值为 FIT_TO_PAGE 和 SIZE_ON_SCREEN。默认值为 FIT_TO_PAGE。

**注：**宽度和高度的最小值（*minWidth* 和 *minHeight*）为 10 mm（约 0.4 英寸）。

*units*

 SymbolicConstant，指定用于边距和图像大小的单位。可选值为 INCHES 和 MM。默认值为 INCHES。

*quality*

 SymbolicConstant，指定图像的质量。可选值为 COARSE、MEDIUM 和 FINE。默认值为 MEDIUM。

*topMargin*

 Float，指定当前选择的单位（英寸或毫米）的纸上边距。可能的值为 *topMargin* ![](../graphics/ker_eqn00407.gif) 0。默认值为 0.5。

*bottomMargin*

 Float，指定当前选择的单位（英寸或毫米）的纸下边距。可能的值为 *bottomMargin* ![](../graphics/ker_eqn00407.gif) 0。默认值为 0.5。

*leftMargin*

 Float，指定当前选择的单位（英寸或毫米）的纸左边距。可能的值为 *leftMargin* ![](../graphics/ker_eqn00407.gif) 0。默认值为 0.5。

*rightMargin*

 Float，指定当前选择的单位（英寸或毫米）的纸右边距。可能的值为 *rightMargin* ![](../graphics/ker_eqn00407.gif) 0。默认值为 0.5。

*orientation*

 SymbolicConstant，指定图像的方向。可选值为 PORTRAIT 和 LANDSCAPE。默认值为 PORTRAIT。

*logo*

 Boolean，指定输出是否包含 Abaqus 徽标。默认值为 ON。

*date*

 Boolean，指定输出是否包含日期。默认值为 ON。

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

### 43.3.2 成员

PageSetupOptions 对象的成员与 [setValues](pt01ch43pyo03.md#ker-pagesetupoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。

