# 23.2 FreeBodyReportOptions 对象





FreeBodyReportOptions 对象存储使用 `writeFreeBodyReport` 方法将自由体计算结果写入 ASCII 文件时的设置。FreeBodyReportOptions 对象没有构造函数。当您导入 Visualization 模块时，Abaqus 会创建 *freeBodyReportOptions* 成员。

**访问**

```
import visualization
session.defaultFreeBodyReportOptions
session.freeBodyReportOptions
```

### 23.2.1 setValues(...)

此方法修改 FreeBodyReportOptions 对象。

**必需参数**

无。

**可选参数**

*numDigits*

一个 Int，指定小数位数。默认值为 3。

*forceThreshold*

一个 Float，指定力的阈值。默认值为 10–6。

*momentThreshold*

一个 Float，指定力矩的阈值。默认值为 10–6。

*numberFormat*

一个 SymbolicConstant，指定数字格式。可能的值为 SCIENTIFIC、FIXED 和 ENGINEERING。默认值为 SCIENTIFIC。

*reportFormat*

一个 SymbolicConstant，指定报告格式。可能的值为 NORMAL_ANNOTATED 和 COMMA_SEPARATED_VALUES。默认值为 NORMAL_ANNOTATED。

*csysType*

一个 SymbolicConstant，指定坐标系类型。可能的值为 GLOBAL 和 LOCAL。默认值为 GLOBAL。

**返回值**

一个 FreeBodyReportOptions 对象。

**异常**

无。

### 23.2.2 成员

FreeBodyReportOptions 对象具有与 [setValues](pt01ch23pyo02.md#ker-freebodyreportoptions-setvalues-pyc) 方法的参数相同的名称和描述的成员。





