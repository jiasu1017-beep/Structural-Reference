# 47.9 NumberFormat 对象





NumberFormat 对象是用于定义某些数字输出格式选项的格式化模板。

**访问**

```
import visualization
session.defaultFieldReportOptions.numberFormat
session.fieldReportOptions.numberFormat
session.journalOptions.defaultFormat
session.journalOptions.fieldReportFormat
session.journalOptions.geometryFormat
```

### 47.9.1 NumberFormat(...)

此方法创建 NumberFormat 对象。

**路径**

```
session.defaultFieldReportOptions.NumberFormat
session.fieldReportOptions.NumberFormat
session.journalOptions.NumberFormat
```

**必要参数**

无。

**可选参数**

*blankPad*

Boolean，指定是否应用空白字符填充打印数字以确保字段大小相等。*blankPad* 参数在打印输出包含列时很有用。默认值为 ON。

*format*

SymbolicConstant，指定格式类型。可能的值为 ENGINEERING、SCIENTIFIC 和 AUTOMATIC。默认值为 ENGINEERING。

*numDigits*

Int，指定结果显示的位数。*numDigits* ![](../graphics/ker_eqn00417.gif)。默认值为 6。

*precision*

Int，指定数字截断显示的小数位数。*precision* ![](../graphics/ker_eqn00418.gif)。如果 *precision* =0，则不应用截断。默认值为 0。

**返回值**

NumberFormat 对象。

**异常**

无。

### 47.9.2 成员

NumberFormat 对象的成员与 [NumberFormat](pt01ch47pyo09.md#ker-numberformat-numberformat-pyc) 方法的参数具有相同的名称和描述。


