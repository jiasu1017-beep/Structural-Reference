# 40.7 HistoryVariable 对象

HistoryVariable 对象存储历史数据。

**访问**

```
import visualization
session.odbData[*name*].historyVariables[*i*]
```

### 40.7.1 成员

HistoryVariable 对象具有以下成员：

*name*

 String，指定历史请求标签。此字符串为只读。

*legendLabel*

 String，指定图例文本。此字符串为只读。

*steps*

 (String, Int, SymbolicConstant) 元组的元组，指定步骤。此序列为只读。每个内部序列包含以下元素：
- *stepLabel*：字符串，指定步骤标签。
- *stepNumber*：Int，指定步骤编号。
- *procedureDomain*：SymbolicConstant，指定步骤的分析类型，可以是 "TIME"、"FREQUENCY" 或 "MODAL"。

