# 34.8 HistoryOutput 对象

HistoryOutput 对象包含指定变量在一点的历史输出。

**访问**

```
import odbAccess
session.odbs[*name*].steps[*name*].historyRegions[*name*]\
.historyOutputs[*name*]
```

### 34.8.1 HistoryOutput(...)

此方法创建 a HistoryOutput 对象。

**路径**

```
session.odbs[*name*].steps[*name*].historyRegions[*name*].HistoryOutput
```

**必要参数**

*name*

一个字符串，指定输出变量名称。

*description*

一个字符串，指定输出变量。

*type*

一个 SymbolicConstant，指定输出类型。当前仅支持 SCALAR。

**可选参数**

*validInvariants*

SymbolicConstant 序列，指定应该为此场计算的不变量。可能的值为 MAGNITUDE、MISES、TRESCA、PRESS、INV3、MAX_PRINCIPAL、MID_PRINCIPAL 和 MIN_PRINCIPAL。默认值为空序列。

**返回值**

HistoryOutput 对象。

**异常**

无。

### 34.8.2 addData(...)

此方法向 HistoryOutput 对象的 *data* 成员添加数据。

**必要参数**

*frame*

一个 Double，指定帧值。*frame* 可以指定为步时间、频率或模式号。

*value*

一个 Double，指定在 *frame* 中指定的帧值处变量的值。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 34.8.3 addData(...)

此方法向 HistoryOutput 对象的 *data* 成员添加数据。

**必要参数**

*frame*

浮点数序列，指定帧值。*frame* 可以指定为步时间、频率或模式号。

*value*

浮点数序列，指定在 *frame* 中指定的帧值处变量的值。

**可选参数**

无。

**返回值**

无

**异常**

如果 *frame* 的长度与 *value* 的长度不同，则引发 ValueError。

### 34.8.4 addData(...)

此方法向 HistoryOutput 对象的 *data* 成员添加数据。

**必要参数**

*data*

浮点数对序列，指定对（*frameValue*、*value*），其中 *frameValue* 是时间、频率或模式，*value* 是指定变量在 *frameValue* 处的值。（此值取决于变量的类型。）

**可选参数**

无。

**返回值**

无

**异常**

无。

### 34.8.5 成员

HistoryOutput 对象具有与 [HistoryOutput](pt01ch34pyo08.md#ker-historyoutput-historyoutput-pyc) 方法的参数名称和描述相同的成员。

此外，HistoryOutput 对象具有以下成员：

*data*

浮点数对元组，指定对（*frameValue*、*value*），其中 *frameValue* 是时间、频率或模式，*value* 是指定变量在 *frameValue* 处的值。（此值取决于变量的类型。）

*conjugateData*

浮点数对元组，指定每个帧值（时间、频率或模式）处指定复变量的虚部。对的形式为（*frameValue*、*value*）。
