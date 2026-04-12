# 61.31 UserXYData 对象

UserXYData 对象存储数据对序列和关于轴的信息。

**访问**

```
Api.userData().xyDataObjects()[*name*]
```

### 61.31.1 addData(...)

此方法替换 [XYData](#ker-xydata-cpp) 对象 *data* 成员的内容。

**原型**

```
void
addData(const odb_SequenceSequenceDouble& data);
```

**必需参数**

*data*

一个 odb_SequenceSequenceDouble，指定 *X–Y* 数据对。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 61.31.2 getData()

返回 [XYData](#ker-xydata-cpp) 对象 *data* 成员的内容。

**原型**

```
odb_SequenceSequenceFloat
getData();
```

**参数**

无。

**返回值**

一个 odb_SequenceSequenceFloat。

**异常**

无。

### 61.31.3 成员

UserXYData 对象可以具有以下成员：

**原型**

```
odb_String name() const;
odb_String sourceDescription() const;
odb_String contentDescription() const;
odb_String positionDescription() const;
odb_String xAxisLabel() const;
odb_String yAxisLabel() const;
odb_String legendLabel() const;
odb_String description() const;
odb_SequenceSequenceDouble data() const;
```

*name*

一个 odb_String，指定存储库键。

*sourceDescription*

一个 odb_String，指定 *X–Y* 数据的来源（例如，"Entered from keyboard"、"Taken from ASCII file"、"Read from an ODB" 等）。默认值为空字符串。

*contentDescription*

一个 odb_String，指定 *X–Y* 数据的内容（例如，"field 1 vs. field 2"）。默认值为空字符串。

*positionDescription*

一个 odb_String，指定关于 *X–Y* 数据的附加信息（例如，"for whole model"）。默认值为空字符串。

*xAxisLabel*

一个 odb_String，指定 X 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能会被覆盖。默认值为空字符串。

*yAxisLabel*

一个 odb_String，指定 Y 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能会被覆盖。默认值为空字符串。

*legendLabel*

一个 odb_String，指定图例中使用的标签。默认值为 XYData 对象的名称。

*description*

一个 odb_String，指定 XYData 对象的完整描述。

*data*

一个 odb_SequenceSequenceDouble，指定 *X–Y* 数据对。
