# 34.10 HistoryRegion 对象

HistoryRegion 对象包含模型中单个位置的历史数据。

**访问**

```
import odbAccess
session.odbs[*name*].steps[*name*].historyRegions[*name*]
```

### 34.10.1 HistoryRegion(...)

此方法创建 a HistoryRegion 对象。

**路径**

```
session.odbs[*name*].steps[*name*].HistoryRegion
```

**必要参数**

*name*

一个字符串，指定 HistoryRegion 对象的名称。

*description*

一个字符串，指定 HistoryRegion 对象的描述。

*point*

一个 [HistoryPoint](pt01ch34pyo09.md) 对象，指定历史数据所引用的点。

**可选参数**

*loadCase*

`None` 或一个 [OdbLoadCase](pt01ch34pyo16.md) 对象，指定与 HistoryRegion 对象关联的负载情况。默认值为 `None`。

**返回值**

HistoryRegion 对象。

**异常**

无。

### 34.10.2 getSubset(...)

此方法返回 HistoryRegion 对象中数据的子集。

**必要参数**

*variableName*

一个字符串，指定要返回的输出变量名称。

**可选参数**

无。

**返回值**

HistoryRegion 对象。

**异常**

无。

### 34.10.3 getSubset(...)

此方法返回 HistoryRegion 对象中数据的子集。

**必要参数**

*start*

一个 Float，指定子集的起点。这与 [HistoryOutput](pt01ch34pyo08.md) 对象的数据数组成员的第一个项目相同。

**可选参数**

无。

**返回值**

HistoryRegion 对象。

**异常**

无。

### 34.10.4 getSubset(...)

此方法返回 HistoryRegion 对象中数据的子集。

**必要参数**

*start*

一个 Float，指定子集的起点。这与 [HistoryOutput](pt01ch34pyo08.md) 对象的数据数组成员的第一个项目相同。

*end*

一个 Float，指定子集的终点。

**可选参数**

无。

**返回值**

HistoryRegion 对象。

**异常**

无。

### 34.10.5 成员

HistoryRegion 对象具有与 [HistoryRegion](pt01ch34pyo10.md#ker-historyregion-historyregion-pyc) 方法的参数名称和描述相同的成员。

此外，HistoryRegion 对象可以具有以下成员：

*position*

一个 SymbolicConstant，指定历史输出的位置。可能的值为 NODAL、INTEGRATION_POINT、WHOLE_ELEMENT、WHOLE_REGION 和 WHOLE_MODEL。

*historyOutputs*

[HistoryOutput](pt01ch34pyo08.md) 对象的仓库。
