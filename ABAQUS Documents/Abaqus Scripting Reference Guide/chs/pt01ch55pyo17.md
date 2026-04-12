# 55.17 XYReportOptions 对象







XYReportOptions 对象存储在将 [XYData](pt01ch55pyo01.md) 对象写入 ASCII 文件时 `writeXYReport` 方法使用的设置。XYReportOptions 对象没有构造函数。当您导入 Visualization 模块时，Abaqus 会创建 *xyReportOptions* 成员。

**访问**

```
import visualization
session.defaultXYReportOptions
session.xyReportOptions
```

### 55.17.1 setValues(...)

此方法修改 XYReportOptions 对象。

**必需参数**

None。

**可选参数**

*pageWidth*

一个 Int，指定当 *pageWidthLimited*=ON 时报表文件每行的字符数。可能的值为 *pageWidth* ![](../graphics/ker_eqn00060.gif) 0。默认值为 80。

*numDigits*

一个 Int，指定报表文件中每个数据值要包含的有效数字位数。可能的值为 0 ![](../graphics/ker_eqn00013.gif) *numDigits* ![](../graphics/ker_eqn00013.gif) 9。默认值为 6。

*interpolation*

一个 Boolean，指定是否对缺失数据值执行线性插值。默认值为 OFF。

*xyData*

一个 Boolean，指定是否打印所选 XYData 对象的 *X* 和 *Y* 值。（如果 *xyData*=OFF，仍可以打印 *totals* 和 *minMax*。）默认值为 ON。

*totals*

一个 Boolean，指定是否打印所选 XYData 对象的 *Y* 值之和。默认值为 OFF。

*minMax*

一个 Boolean，指定是否打印所选 XYData 对象的最小和最大 *X* 和 *Y* 值。默认值为 OFF。

*pageWidthLimited*

一个 Boolean，指定是否限制页面宽度。默认值为 OFF。

*numberFormat*

一个 SymbolicConstant，指定报告 XYData 对象时要使用的数字格式。可能的值为 AUTOMATIC、ENGINEERING 和 SCIENTIFIC。默认值为 ENGINEERING。

*layout*

一个 SymbolicConstant，指定报告 XYData 对象时要使用的格式。可能的值为 SINGLE_TABLE 和 SEPARATE_TABLES。默认值为 SINGLE_TABLE。

**返回值**

None

**异常**

RangeError。

如果 *xyData*、*total* 和 *minMax* 都为 OFF：

```
At least one of the data print methods must be selected
```

### 55.17.2 成员

XYReportOptions 对象具有与 [setValues](pt01ch55pyo17.md#ker-xyreportoptions-setvalues-pyc) 方法的参数具有相同名称和描述的成员。

