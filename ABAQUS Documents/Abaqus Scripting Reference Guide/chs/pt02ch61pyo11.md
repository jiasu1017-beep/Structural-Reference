# 61.11 HistoryRegion 对象

HistoryRegion 对象包含模型中单个位置的历史数据。

**访问**

```
odb.steps()[*name*].historyRegions()[*name*]
```

### 61.11.1 HistoryRegion(...)

此方法创建一个 HistoryRegion 对象。

**路径**

```
odb.steps()[*name*].HistoryRegion
```

**原型**

```
odb_HistoryRegion&
HistoryRegion(const odb_String& name,
              const odb_String& description,
              const odb_HistoryPoint& point,
              const odb_LoadCase& loadCase);
```

**必需参数**

*name*

一个 odb_String，指定 HistoryRegion 对象的名称。

*description*

一个 odb_String，指定 HistoryRegion 对象的描述。

*point*

一个 [HistoryPoint](pt02ch61pyo10.md) 对象，指定历史数据所指向的点。

**可选参数**

*loadCase*

一个 [OdbLoadCase](pt02ch61pyo17.md) 对象，指定与 HistoryRegion 对象关联的载荷工况。

**返回值**

一个 HistoryRegion 对象。

**异常**

无。

### 61.11.2 getSubset(...)

此方法返回 HistoryRegion 对象中数据的子集。

**原型**

```
odb_HistoryRegion
getSubset(const odb_String& variableName);
```

**必需参数**

*variableName*

一个 String，指定要返回的输出变量名称。

**可选参数**

无。

**返回值**

一个 HistoryRegion 对象。

**异常**

无。

### 61.11.3 getSubset(...)

此方法返回 HistoryRegion 对象中数据的子集。

**原型**

```
odb_HistoryRegion
getSubset(float start);
```

**必需参数**

*start*

一个 Float，指定子集的起始位置。这与 [HistoryOutput](pt02ch61pyo09.md) 对象的数据数组成员的第一个元素相同。

**可选参数**

无。

**返回值**

一个 HistoryRegion 对象。

**异常**

无。

### 61.11.4 getSubset(...)

此方法返回 HistoryRegion 对象中数据的子集。

**原型**

```
odb_HistoryRegion
getSubset(float start,
          float end);
```

**必需参数**

*start*

一个 Float，指定子集的起始位置。这与 [HistoryOutput](pt02ch61pyo09.md) 对象的数据数组成员的第一个元素相同。

*end*

一个 Float，指定子集的结束位置。

**可选参数**

无。

**返回值**

一个 HistoryRegion 对象。

**异常**

无。

### 61.11.5 成员

HistoryRegion 对象具有与 [HistoryRegion](pt02ch61pyo11.md#ker-historyregion-historyregion-cpp) 方法参数相同名称和描述的成员。

此外，HistoryRegion 对象可以具有以下成员：

**原型**

```
odb_String description() const;
const odb_LoadCase& loadCase() const;
odb_String name() const;
odb_HistoryPoint point() const;
odb_Enum::odb_ResultPositionEnum position() const;
const odb_HistoryOutputRepository& historyOutputs();
```

*position*

一个 odb_Enum::odb_ResultPositionEnum，指定历史输出的位置。可能的值为 odb_Enum::NODAL、odb_Enum::INTEGRATION_POINT、odb_Enum::WHOLE_ELEMENT、odb_Enum::WHOLE_REGION 和 odb_Enum::WHOLE_MODEL。

*historyOutputs*

[HistoryOutput](pt02ch61pyo09.md) 对象的存储库。
