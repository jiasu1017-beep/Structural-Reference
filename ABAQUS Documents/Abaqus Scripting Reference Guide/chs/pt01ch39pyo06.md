# 39.6 ProbeReport 对象

ProbeReport 对象用于存储与探测数据表格报告相关的设置。ProbeReport 对象没有构造函数。导入 Visualization 模块时，Abaqus 会创建 *defaultProbeReport* 和 *probeReport* 成员。首次启动探测时，*probeReport* 成员的值使用 *defaultProbeReport* 成员的值进行初始化。

**访问**

```
import visualization
session.defaultProbeReport
session.probeReport
```

### 39.6.1 setValues(...)

此方法修改 ProbeReport 对象。

**必需参数**

无。

**可选参数**

*options*

 `None` 或 ProbeReport 对象，指定要复制的值。如果还有其他参数提供给 `setValues`，它们将覆盖 *options* 中的值。默认值为 `None`。

*numColumns*

 Int，指定报告文件中的列数。此参数仅在 *pageWidth*=SPECIFY 时有效。默认值为 80。

*numDigits*

 Int，指定小数值的有效数字位数。默认值为 6。

*numFormat*

 SymbolicConstant，指定格式化小数值时使用的数字格式。可选值为 AUTOMATIC、ENGINEERING 和 SCIENTIFIC。默认值为 ENGINEERING。

*pageWidth*

 SymbolicConstant，指定页面宽度格式。可选值为 NO_LIMIT 和 SPECIFY。默认值为 NO_LIMIT。

*printTotal*

 Boolean，指定是否打印场输出结果（当 *probeObject*="ODB" 时）或 *x* 和 *y* 坐标（当 *probeObject*="XYPlot" 时）的总值。默认值为 OFF。

*printMinMax*

 Boolean，指定是否打印场输出结果（当 *probeObject*="ODB" 时）或 *x* 和 *y* 坐标（当 *probeObject*="XYPlot" 时）的最小值和最大值。默认值为 OFF。

**返回值**

无

**异常**

无。

### 39.6.2 成员

ProbeReport 对象的成员与 [setValues](pt01ch39pyo06.md#ker-probereport-setvalues-pyc) 方法的参数具有相同的名称和描述。

