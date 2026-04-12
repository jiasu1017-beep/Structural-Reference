# 43.1 PrintOptions 对象

PrintOptions 对象存储 Abaqus 用于所有打印方法的通用设置。PrintOptions 对象没有构造函数。启动会话时，Abaqus 会创建 *printOptions* 成员。

**访问**

```
session.printOptions
```

### 43.1.1 setValues(...)

此方法修改 PrintOptions 对象。

**必需参数**

无。

**可选参数**

*rendition*

 SymbolicConstant，指定图像的渲染方式。可选值为 BLACK_AND_WHITE、GREYSCALE 和 COLOR。默认值为 COLOR。

*vpDecorations*

 Boolean，指定输出是否包含视口边框和标题。默认值为 ON。

*vpBackground*

 Boolean，指定输出是否包含视口背景。默认值为 OFF。

*compass*

 Boolean，指定输出是否包含视口罗盘。默认值为 OFF。

*printCommand*

 String，指定将由 `printToPrinter` 方法使用的默认打印命令（如果没有提供 *printCommand* 参数）。默认值为 "lpr"。

*deleteTemporaryFiles*

 Boolean，指定是否删除打印图像时创建的临时文件。默认值为 ON。

如果您的打印机不支持打印假脱机，您应该将 *deleteTemporaryFiles* 参数设置为 False。

*reduceColors*

 Boolean，指定是否将打印的光栅图像从真彩色减少到 256 色以减小文件大小。图像质量会受到影响。默认值为 OFF。

**返回值**

无

**异常**

无。

### 43.1.2 成员

PrintOptions 对象的成员与 [setValues](pt01ch43pyo01.md#ker-printoptions-setvalues-pyc) 方法的参数具有相同的名称和描述。

