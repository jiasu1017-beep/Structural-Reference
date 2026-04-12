# 51.2 FieldOutputRequest 对象

FieldOutputRequest 对象用于定义场输出请求。

**访问**

```
import step
mdb.models[*name*].fieldOutputRequests[*name*]
```

### 51.2.1 FieldOutputRequest(...)

此方法创建一个 FieldOutputRequest 对象。

**路径**

```
mdb.models[*name*].FieldOutputRequest
```

**必要参数**

*name*

一个 String，指定仓库键。

*createStepName*

一个 String，指定创建该对象的步骤名称。

**可选参数**

*region*

 SymbolicConstant MODEL 或一个 [Region](pt01ch45pyo03.md) 对象，指定请求输出的区域。SymbolicConstant MODEL 代表整个模型。默认值为 MODEL。

*variables*

一个 String 序列，指定输出请求的变量或分量名称，或 SymbolicConstant PRESELECT 或 ALL。PRESELECT 代表给定步骤的所有默认输出变量。ALL 代表所有有效的输出变量。默认值为 PRESELECT。

*frequency*

SymbolicConstant LAST_INCREMENT 或一个 Int，指定输出频率（以增量计）。默认值为 1。

*modes*

SymbolicConstant ALL 或一个 Int 序列，指定需要输出的特征模态列表。默认值为 ALL。

*timeInterval*

SymbolicConstant EVERY_TIME_INCREMENT 或一个 Float，指定写入输出状态的时间间隔。默认值为 EVERY_TIME_INCREMENT。

*numIntervals*

一个 Int，指定在步骤期间写入输出数据库状态的间隔数。默认值为 20。

*timeMarks*

一个 Boolean，指定何时将结果写入输出数据库。OFF 表示在指定间隔数规定的时间之后立即写入输出。ON 表示在指定间隔数规定的确切时间写入输出。默认值为 OFF。

*boltLoad*

一个 String，指定请求输出的螺栓载荷。

*sectionPoints*

SymbolicConstant DEFAULT 或一个 Int 序列，指定请求输出的截面点。默认值为 DEFAULT。

*interactions*

 `None` 或一个 String 序列，指定相互作用名称。默认值为 `None`。

该序列只能包含一个 String。

*rebar*

一个 SymbolicConstant，指定是否为钢筋请求输出。可选值为 EXCLUDE、INCLUDE 和 ONLY。默认值为 EXCLUDE。

*filter*

SymbolicConstant ANTIALIASING 或一个 String，指定输出过滤器对象的名称。默认值为 `None`。

*directions*

一个 Boolean，指定是否输出局部材料坐标系的方向。默认值为 ON。

*fasteners*

一个 String，指定紧固件名称。默认值为空字符串。

*assembledFastener*

一个 String，指定组装紧固件名称。默认值为空字符串。

*assembledFastenerSet*

一个 String，指定由组装紧固件 *assembledFastener* 引用的模型中的集合名称。默认值为空字符串。

*exteriorOnly*

一个 Boolean，指定输出域是否限制在模型的外表面。此参数仅在 *region*=MODEL 时有效。默认值为 OFF。

**返回的值**

一个 FieldOutputRequest 对象。

**异常**

无。

### 51.2.2 deactivate(...)

此方法在指定步骤及其所有后续步骤中停用场输出请求。

**必要参数**

*stepName*

一个 String，指定停用场输出请求的步骤名称。

**可选参数**

无。

**返回的值**

无。

**异常**

TextError。

### 51.2.3 move(...)

此方法将场输出请求状态对象从一个步骤移动到另一个步骤。

**必要参数**

*fromStepName*

一个 String，指定从中移动场输出请求状态的步骤名称。

*toStepName*

一个 String，指定场输出请求状态要移动到的步骤名称。

**可选参数**

无。

**返回的值**

无。

**异常**

TextError。

### 51.2.4 reset(...)

此方法将指定步骤的场输出请求状态重置为前一步骤的状态。

**必要参数**

*stepName*

一个 String，指定重置场输出请求状态的步骤名称。

**可选参数**

无。

**返回的值**

无。

**异常**

TextError。

### 51.2.5 resume()

此方法恢复之前被抑制的场输出请求。

**参数**

无。

**返回的值**

无。

**异常**

TextError。

### 51.2.6 suppress()

此方法抑制场输出请求。

**参数**

无。

**返回的值**

无。

**异常**

TextError。

### 51.2.7 setValues(...)

此方法修改创建 FieldOutputRequest 对象的步骤中现有对象的数据。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [FieldOutputRequest](pt01ch51pyo02.md#ker-fieldoutputrequest-fieldoutputrequest-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回的值**

无。

**异常**

无。

### 51.2.8 setValuesInStep(...)

此方法修改指定步骤中现有 FieldOutputRequest 对象的传播数据。

**必要参数**

*stepName*

一个 String，指定修改场输出请求的步骤名称。

**可选参数**

*variables*

一个 String 序列，指定输出请求的变量或分量名称，或 SymbolicConstant PRESELECT 或 ALL。PRESELECT 代表给定步骤的所有默认输出变量。ALL 代表所有有效的输出变量。

*frequency*

SymbolicConstant LAST_INCREMENT 或一个 Int，指定输出频率（以增量计）。默认值为 1。

*modes*

SymbolicConstant ALL 或一个 Int 序列，指定需要输出的特征模态列表。默认值为 ALL。

*timeInterval*

SymbolicConstant EVERY_TIME_INCREMENT 或一个 Float，指定写入输出状态的时间间隔。默认值为 EVERY_TIME_INCREMENT。

*numIntervals*

一个 Int，等于在步骤期间写入输出数据库状态的间隔数。默认值为 20。

*timePoints*

一个 String，指定时间点对象的名称。默认值为在步骤期间写入输出数据库状态的间隔数。默认值为 `None`。

*timeMarks*

一个 Boolean，指定何时将结果写入输出数据库。默认值为 OFF。

**返回的值**

无。

**异常**

无。

### 51.2.9 成员

FieldOutputRequest 对象可以具有以下成员：

*boltLoad*

一个 String，指定请求输出的螺栓载荷。

*region*

 SymbolicConstant MODEL 或一个 [Region](pt01ch45pyo03.md) 对象，指定请求输出的区域。SymbolicConstant MODEL 代表整个模型。默认值为 MODEL。

*interactions*

 `None` 或一个 String 元组，指定相互作用名称。默认值为 `None`。

该序列只能包含一个 String。

### 51.2.10 对应的分析关键字

| [*CONTACT OUTPUT](../key/key-link.md#usb-kws-hcontactoutput) |
| --- |
| [*ELEMENT OUTPUT](../key/key-link.md#usb-kws-helementoutput) |
| [*ENERGY OUTPUT](../key/key-link.md#usb-kws-henergyoutput) |
| [*INCREMENTATION OUTPUT](../key/key-link.md#usb-kws-hincrementationoutput) |
| [*MODAL OUTPUT](../key/key-link.md#usb-kws-hmodaloutput) |
| [*NODE OUTPUT](../key/key-link.md#usb-kws-hnodeoutput) |
| [*OUTPUT](../key/key-link.md#usb-kws-houtput) |
| [*RADIATION OUTPUT](../key/key-link.md#usb-kws-hradiationoutput) |
