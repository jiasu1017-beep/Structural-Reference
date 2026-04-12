# 51.4 HistoryOutputRequest 对象

HistoryOutputRequest 对象用于定义历史输出请求。

**访问**

```
import step
mdb.models[*name*].historyOutputRequests[*name*]
```

### 51.4.1 HistoryOutputRequest(...)

此方法创建一个 HistoryOutputRequest 对象。

**路径**

```
mdb.models[*name*].HistoryOutputRequest
```

**必要参数**

*name*

一个 String，指定仓库键。

*createStepName*

一个 String，指定创建该对象的步骤名称。

**可选参数**

*region*

 SymbolicConstant MODEL 或一个 [Region](pt01ch45pyo03.md) 对象，指定请求输出的区域。SymbolicConstant MODEL 代表整个模型。默认值为 MODEL。

如果该区域是表面区域，则该表面必须位于通用接触表面域内。

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

*boltLoad*

一个 String，指定请求输出的螺栓载荷。默认值为空字符串。

*sectionPoints*

SymbolicConstant DEFAULT 或一个 Int 序列，指定请求输出的截面点。默认值为 DEFAULT。

*stepName*

一个 String，指定步骤名称。默认值为空字符串。

*interactions*

 `None` 或一个 String 序列，指定相互作用名称。默认值为 `None`。

该序列只能包含一个 String。

*contourIntegral*

一个 String，指定轮廓积分名称。默认值为 `None`。

*numberOfContours*

一个 Int，指定为轮廓积分对象输出的轮廓积分数量。默认值为 0。

*stressInitializationStep*

一个 String，指定应力初始化步骤的名称。默认值为 `None`。

*contourType*

一个 SymbolicConstant，指定轮廓积分的类型。可选值为 J_INTEGRAL、C_INTEGRAL、T_STRESS 和 K_FACTORS。默认值为 J_INTEGRAL。

*kFactorDirection*

一个 SymbolicConstant，指定应力强度因子方向。可选值为 MTS、MERR 和 K110。*kFactorDirection* 参数仅在 *contourType*=K_FACTORS 时有效。默认值为 MTS。

*rebar*

一个 SymbolicConstant，指定是否为钢筋请求输出。可选值为 EXCLUDE、INCLUDE 和 ONLY。默认值为 EXCLUDE。

*integratedOutputSection*

一个 String，指定集成输出截面。默认值为空字符串。

*springs*

一个 String 序列，指定弹簧/阻尼器名称。默认值为 `None`。该序列只能包含一个 String。

*filter*

SymbolicConstant ANTIALIASING 或一个 String，指定输出过滤器对象的名称。默认值为 `None`。

*fasteners*

一个 String，指定紧固件名称。默认值为空字符串。

*assembledFastener*

一个 String，指定组装紧固件名称。默认值为空字符串。

*assembledFastenerSet*

一个 String，指定由组装紧固件 *assembledFastener* 引用的模型中的集合名称。默认值为空字符串。

*sensor*

一个 Boolean，指定是否将输出请求与传感器定义关联。默认值为 OFF。

*useGlobal*

一个 Boolean，指定是否在全局方向上输出向量值节点变量。默认值为 True。

**返回的值**

一个 HistoryOutputRequest 对象。

**异常**

无。

### 51.4.2 deactivate(...)

此方法在指定步骤及其所有后续步骤中停用历史输出请求。

**必要参数**

*stepName*

一个 String，指定停用历史输出请求的步骤名称。

**可选参数**

无。

**返回的值**

无。

**异常**

TextError。

### 51.4.3 move(...)

此方法将历史输出请求状态对象从一个步骤移动到另一个步骤。

**必要参数**

*fromStepName*

一个 String，指定从中移动历史输出请求状态的步骤名称。

*toStepName*

一个 String，指定历史输出请求状态要移动到的步骤名称。

**可选参数**

无。

**返回的值**

无。

**异常**

TextError。

### 51.4.4 reset(...)

此方法将指定步骤的历史输出请求状态重置为前一步骤的状态。

**必要参数**

*stepName*

一个 String，指定重置历史输出请求状态的步骤名称。

**可选参数**

无。

**返回的值**

无。

**异常**

TextError。

### 51.4.5 resume()

此方法恢复之前被抑制的历史输出请求。

**参数**

无。

**返回的值**

无。

**异常**

TextError。

### 51.4.6 suppress()

此方法抑制历史输出请求。

**参数**

无。

**返回的值**

无。

**异常**

TextError。

### 51.4.7 setValues(...)

此方法修改创建 HistoryOutputRequest 对象的步骤中现有对象的数据。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [HistoryOutputRequest](pt01ch51pyo04.md#ker-historyoutputrequest-historyoutputrequest-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回的值**

无。

**异常**

无。

### 51.4.8 setValuesInStep(...)

此方法修改指定步骤中现有 HistoryOutputRequest 对象的传播数据。

**必要参数**

*stepName*

一个 String，指定修改历史输出请求的步骤名称。

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

一个 Int，指定在步骤期间写入输出数据库状态的间隔数。默认值为 20。

*timePoints*

一个 String，指定时间点对象的名称。默认值为在步骤期间写入输出数据库状态的间隔数。默认值为 `None`。

**返回的值**

无。

**异常**

无。

### 51.4.9 成员

HistoryOutputRequest 对象可以具有以下成员：

*boltLoad*

一个 String，指定请求输出的螺栓载荷。默认值为空字符串。

*region*

 SymbolicConstant MODEL 或一个 [Region](pt01ch45pyo03.md) 对象，指定请求输出的区域。SymbolicConstant MODEL 代表整个模型。默认值为 MODEL。

如果该区域是表面区域，则该表面必须位于通用接触表面域内。

*sectionPoints*

SymbolicConstant DEFAULT 或一个 Int 元组，指定请求输出的截面点。默认值为 DEFAULT。

*interactions*

 `None` 或一个 String 元组，指定相互作用名称。默认值为 `None`。

该序列只能包含一个 String。

### 51.4.10 对应的分析关键字

| [*CONTACT OUTPUT](../key/key-link.md#usb-kws-hcontactoutput) |
| --- |
| [*ELEMENT OUTPUT](../key/key-link.md#usb-kws-helementoutput) |
| [*ENERGY OUTPUT](../key/key-link.md#usb-kws-henergyoutput) |
| [*INCREMENTATION OUTPUT](../key/key-link.md#usb-kws-hincrementationoutput) |
| [*MODAL OUTPUT](../key/key-link.md#usb-kws-hmodaloutput) |
| [*NODE OUTPUT](../key/key-link.md#usb-kws-hnodeoutput) |
| [*OUTPUT](../key/key-link.md#usb-kws-houtput) |
| [*RADIATION OUTPUT](../key/key-link.md#usb-kws-hradiationoutput) |
