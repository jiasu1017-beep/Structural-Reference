# 4.8 Session 对象





以下命令对 Session 对象进行操作。有关 Session 对象的更多信息，请参见["Session 对象"，第 47.1 节](pt01ch47pyo01.md)。

**访问**

```
import animation
```

### 4.8.1 writeImageAnimation(...)

此方法将画布对象列表中存在的动画写入文件。它使用给定的文件名和文件格式生成动画文件，并使用适当选项对象中的值。

**必需参数**

*fileName*

一个 String，指定要生成的动画文件的名称。

*format*

一个 SymbolicConstant，指定生成文件的格式。可能的值为 AVI、QUICKTIME、VRML 和 COMPRESSED_VRML。

**可选参数**

*canvasObjects*

一个序列，指定要捕获的画布对象。默认行为是捕获所有画布对象。

**返回值**

无

**异常**

无。




