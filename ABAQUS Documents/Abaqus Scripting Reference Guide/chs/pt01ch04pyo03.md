# 4.3 AVIOptions 对象





AVIOptions 对象用于存储在生成 AVI 动画时要使用的值和属性。AVIOptions 对象没有构造函数。导入动画模块时，Abaqus 创建 *aviOptions* 成员。

**访问**

```
import animation
session.aviOptions
```

### 4.3.1 setValues(...)

此方法修改 AVIOptions 对象。

**必需参数**

无。

**可选参数**

*compressionMethod*

一个 SymbolicConstant，指定 AVI 格式的压缩方法。可能的值为：
- RAW8，指定每像素 8 位的未压缩格式。
- RAW32，指定每像素 32 位的未压缩格式。
- RLE8，指定每像素 8 位的行程长度编码格式。
- CODEC，指定由 CODEC（编码器/解码器）定义的格式。CODEC 的可用性取决于系统。

默认值为 RLE8。

*compressionQuality*

一个 Int，当 *compressionMethod* 设置为 CODEC 时，指定压缩质量百分比。

*codecOptions*

一个 String，当 *compressionMethod* 设置为 CODEC 时，指定定义 CODEC 的系统特定选项。

*sizeDefinition*

一个 SymbolicConstant，指定如何指定图像的宽度和高度。可能的值为 SIZE_ON_SCREEN 和 USER_DEFINED。默认值为 SIZE_ON_SCREEN。

*imageSize*

一对 Int，指定当 *sizeDefinition*=USER_DEFINED 时图像的宽度和高度（以像素为单位）。可能的 Int 值范围为 (*minWidth*, *minHeight*) ![](../graphics/ker_eqn00013.gif) (width, height) ![](../graphics/ker_eqn00013.gif) (*maxWidth*, *maxHeight*)。默认值为屏幕大小。

**注：**最小宽度（*minWidth*）和高度（*minHeight*）的值取决于以下因素：
- 视口字体大小，
- 是否打印装饰，
- 装饰大小，以及
- 屏幕分辨率。

最小宽度和高度通常小于 50 像素。最大宽度（*maxWidth*）和高度（*maxHeight*）的值取决于系统的图形能力。最大宽度和高度至少与屏幕尺寸一样大。

**返回值**

无

**异常**

无。

### 4.3.2 成员

AVIOptions 对象具有与 [setValues](pt01ch04pyo03.md#ker-avioptions-setvalues-pyc) 方法参数相同名称和描述的成员。




