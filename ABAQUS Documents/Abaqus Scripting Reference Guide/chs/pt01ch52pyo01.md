# 52.1 redentABQ 模块

Python 模块 redentABQ 是 Python redent 模块的包装器。该模块使 Python 文本文件中的缩进保持一致。

该模块可以使用以下语句从命令提示符作为脚本运行：

`abaqus Python -m redentABQ [options] pathToFile`

其中，以下选项可用于自定义 redentABQ 过程：
- `-b`：如果进行了任何修改，则创建所选文件的备份。
- `-i`：指定要使用的空格数。
- `-t`：在任何更改后测试新缩进的文件。

有关运行 **abaqus Python** 执行过程的更多信息，请参阅《Abaqus Analysis User's Guide》第 3.2.9 节"Python execution"。

**访问**

```
import redentABQ
```

### 52.1.1 indentFile(...)

此方法将缩进后的文件输出到终端窗口，或备份指定文件并替换它。

**必要参数**

*path*

一个 String，指定要处理的文件。

**可选参数**

*indent*

一个 String，指定要使用的缩进量。默认值为四个空格的缩进。自定义缩进字符串必须用引号（`" "`）括起来。

*backup*

一个 Boolean，指定如果在 *path* 参数中指定的文件进行了更改，是否备份该文件。默认值为 False。

*runTest*

一个 Boolean，指定是否测试新缩进的文件以确保其在任何更改后语义相同。默认值为 False。

**返回的值**

一个 Boolean。如果缩进成功，则为 True；否则为 False。

**异常**

无。
