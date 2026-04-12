# 47.6 JournalOptions 对象





JournalOptions 对象指定如何在日志和重放文件中记录几何选择。*journalOptions* 还可用于设置字段报告输出、几何命令输出和其他数字输出的默认格式的数值格式选项。JournalOptions 对象没有构造函数。Abaqus 在会话启动时创建 *journalOptions* 成员。

**访问**

```
session.journalOptions
```

### 47.6.1 setValues(...)

此方法修改 JournalOptions 对象。

**必要参数**

无。

**可选参数**

*replayGeometry*

SymbolicConstant，指定重放文件中几何的格式。可能的值为 COORDINATE、INDEX 和 COMPRESSEDINDEX。默认值为 COMPRESSEDINDEX。

*recoverGeometry*

SymbolicConstant，指定恢复文件中几何的格式。可能的值为 COORDINATE、INDEX 和 COMPRESSEDINDEX。默认值为 COMPRESSEDINDEX。

*defaultFormat*

[NumberFormat](pt01ch47pyo09.md) 对象，指定数字输出的默认格式。默认值与 [NumberFormat](pt01ch47pyo09.md) 对象的默认值相同。

*fieldReportFormat*

[NumberFormat](pt01ch47pyo09.md) 对象，指定字段报告输出中数字的默认格式。默认值与 [NumberFormat](pt01ch47pyo09.md) 对象的默认值相同。

*geometryFormat*

[NumberFormat](pt01ch47pyo09.md) 对象，指定几何命令输出中数字的默认格式。默认值与 [NumberFormat](pt01ch47pyo09.md) 对象的默认值相同。

**返回值**

无

**异常**

无。

### 47.6.2 成员

JournalOptions 对象的成员与 [setValues](pt01ch47pyo06.md#ker-journaloptions-setvalues-pyc) 方法的参数具有相同的名称和描述。


