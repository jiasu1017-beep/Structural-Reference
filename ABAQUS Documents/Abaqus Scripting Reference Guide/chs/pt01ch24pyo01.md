# 24.1 InputFile 对象





InputFile 对象用于存储 Abaqus 输入文件中的定义。可以使用本节所述的方法创建 InputFile 对象。

**访问**

```
import inpParser
```

### 24.1.1 InputFile(...)

此方法通过读取 Abaqus 输入文件创建 InputFile 对象。

**路径**

```
inpParser.InputFile
```

**必需参数**

*file*

一个 String，指定输入文件的路径。

**可选参数**

*directory*

一个 String，指定包含输入文件的目录路径。

**返回值**

一个 InputFile 对象。

**异常**

无。

### 24.1.2 parse(...)

此方法解析与 InputFile 对象关联的输入文件。

**可选参数**

*organize*

一个 Boolean，指定是否将关键字组织成子选项。默认为 True。

*verbose*

一个 Boolean，指定是否打印详细输出。如果 *verbose* 为 True，则打印有关致命错误的信息。如果未发生致命错误，则没有输出。默认为 False。

*bulk*

一个 Boolean，指定输入文件是否包含需要解析的批量数据。默认为 True。

*usePyArray*

一个 Boolean，指定 `parse` 方法可以为关键字数据值返回 AbaqusNDarray 对象。当预期有大量数值数据（即大型节点数组）时，建议使用选项 `usePyArray=True`。

**返回值**

一个 KeywordSequence 对象。

**异常**

如果您多次解析输入文件，则每次后续解析都会引发 ValueError。

### 24.1.3 成员

InputFile 对象具有以下成员：

*file*

一个 String，指定 Abaqus 输入文件的源文件名。

*directory*

一个 String，指定输入文件所在的目录。

*includes*

一个 String 序列，指定指定输入文件中包含的任何其他输入文件。

*missingIncludes*

一个 String 序列，用于指定指定输入文件中包含但无法找到的输入文件。





