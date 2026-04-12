# 24.2 Keyword 对象





Keyword 对象用于存储 Abaqus 输入文件中的关键字定义。

Keyword 对象通过 `InputFile.parse()` 方法返回。

**访问**

```
import inpParser
```

### 24.2.1 成员

InputFile 对象具有以下成员：

*name*

一个 String，指定关键字的名称。

*parameter*

一个 String Dictionary，指定关键字参数。

*data*

一个序列的序列或一个 AbaqusNDarray 对象，指定关键字数据。叶对象的类型取决于关键字。仅当数据合适且 `InputFile.parse()` 方法使用选项 `usePyArray=True` 调用时，才返回 AbaqusNDarray 对象。当预期有大量数值数据（即大型节点数组）时，建议使用选项 `usePyArray=True`。

*suboptions*

一个 KeywordSequence，指定关键字的子选项。

*comments*

一个 String 序列，指定注释。





