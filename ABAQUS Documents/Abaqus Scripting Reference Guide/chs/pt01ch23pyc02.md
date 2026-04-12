# 23.6 writeFreeBodyReport





此命令将自由体输出报告写入文件。

### 23.6.1 writeFreeBodyReport(...)

此方法将 FreeBody 对象写入用户定义的 ASCII 文件。

**路径**

```
session.writeFreeBodyReport
```

**必需参数**

*fileName*

一个 String，指定要写入自由体输出的文件名。

*append*

一个 Boolean，指定是否将自由体输出追加到现有文件。默认值为 ON。

**可选参数**

*step*

一个 Int，标识要从中获取值的步骤。默认值为当前步骤。

*frame*

一个 Int，标识要从中获取值的帧。默认值为当前帧。

*stepFrame*

一个 SymbolicConstant，指示是从指定帧还是从所有活动帧获取值。可能的值为 SPECIFY 和 ALL。默认值为 SPECIFY。

*odb*

一个 Odb 对象，指定要从中读取数据的输出数据库。





