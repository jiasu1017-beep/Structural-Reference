# 23.1 FieldReportOptions 对象





FieldReportOptions 对象存储使用 `writeFieldReport` 方法将 [FieldOutput](pt01ch34pyo06.md) 对象写入 ASCII 文件时的设置。FieldReportOptions 对象没有构造函数。当您导入 Visualization 模块时，Abaqus 会创建 *fieldReportOptions* 成员。

**访问**

```
import visualization
session.defaultFieldReportOptions
session.fieldReportOptions
```

### 23.1.1 setValues(...)

此方法修改 FieldReportOptions 对象。

**必需参数**

无。

**可选参数**

*numColumns*

一个 Int，指定表格报告的列数。默认值为 80。

*numberFormat*

一个 [NumberFormat](pt01ch47pyo09.md) 对象，指定用于打印数字输出的格式类型、数字位数和精度。

*printXYData*

一个 Boolean，指定是否在表格报告中包含 *X–Y* 数据值。默认值为 ON。

*printTotal*

一个 Boolean，指定是否在表格报告中包含列总计。默认值为 ON。

*printMinMax*

一个 Boolean，指定是否在表格报告中包含列摘要的最小值和最大值。默认值为 ON。

*pageWidth*

一个 SymbolicConstant，指定如何确定表格报告的宽度。可能的值为 NO_LIMIT 和 SPECIFY。默认值为 NO_LIMIT。

*columnLayout*

一个 SymbolicConstant，指定如何在表格报告中呈现值。可能的值为 SINGLE_TABLE 和 SEPARATE_TABLES。默认值为 SINGLE_TABLE。

*sort*

一个 SymbolicConstant，指定在表格报告中对值进行排序的顺序。可能的值为 ASCENDING 和 DESCENDING。默认值为 ASCENDING。

**返回值**

一个 FieldReportOptions 对象。

**异常**

无。

### 23.1.2 成员

FieldReportOptions 对象具有与 [setValues](pt01ch23pyo01.md#ker-fieldreportoptions-setvalues-pyc) 方法的参数相同的名称和描述的成员。





