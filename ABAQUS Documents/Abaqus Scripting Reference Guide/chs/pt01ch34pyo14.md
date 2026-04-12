# 34.14 OdbFrame 对象

OdbFrame 对象的域取自父步骤。

**访问**

```
import odbAccess
session.odbs[*name*].steps[*name*].frames[*i*]
```

### 34.14.1 Frame(...)

此方法创建一个 OdbFrame 对象并将其追加到帧序列。

**路径**

```
session.odbs[*name*].steps[*name*].Frame
```

**必要参数**

*incrementNumber*

一个整数，指定步骤内的帧增量号。基础帧通常增量号为 0，结果从 1 开始。在多个负载情况下，相同的增量号会被复制到每个负载情况。

*frameValue*

一个 Float，指定由 [Step](pt01ch49pyo01.md) 对象的 *domain* 成员决定的单位的值。在时间域中等效于 *stepTime*；在频率域中等效于 *frequency*；在模态域中等效于 *mode*。

**可选参数**

*description*

一个字符串，指定帧的内容。默认值为空字符串。

**返回值**

OdbFrame 对象。

**异常**

无。

### 34.14.2 Frame(...)

此构造函数在频率域中创建一个 OdbFrame 对象并将其追加到帧序列。仅当 *domain*=FREQUENCY 或 *domain*=MODAL 时，构造函数的参数才有效。

**路径**

```
session.odbs[*name*].steps[*name*].Frame
```

**必要参数**

*mode*

一个整数，指定特征模态。此成员仅在 *domain*=MODAL 时有效。

*frequency*

一个 Float，指定频率。此成员仅在 *domain*=FREQUENCY 或 [Step](pt01ch49pyo01.md) 对象的 *procedureType* 成员="FREQUENCY" 时有效。默认值为 0.0。

**可选参数**

*description*

一个字符串，指定帧的内容。默认值为空字符串。

**返回值**

OdbFrame 对象。

**异常**

无。

### 34.14.3 Frame(...)

此构造函数为特定负载情况创建一个 OdbFrame 对象并将其追加到帧序列。

**路径**

```
session.odbs[*name*].steps[*name*].Frame
```

**必要参数**

*loadCase*

一个 [OdbLoadCase](pt01ch34pyo16.md) 对象，指定帧的负载情况。

**可选参数**

*description*

一个字符串，指定帧的内容。默认值为空字符串。

*frequency*

一个 Float，指定频率。此成员仅在 *domain*=FREQUENCY 或 [Step](pt01ch49pyo01.md) 对象的 *procedureType* 成员="FREQUENCY" 时有效。默认值为 0.0。

**返回值**

OdbFrame 对象。

**异常**

无。

### 34.14.4 成员

OdbFrame 对象具有与 [Frame](pt01ch34pyo14.md#ker-odbframe-frame-pyc) 方法的参数名称和描述相同的成员。

此外，OdbFrame 对象可以具有以下成员：

*cyclicModeNumber*

一个整数，指定与此帧上存储的数据关联的循环模式号。只有循环对称模型的频率分析具有循环模式号。

*domain*

一个 SymbolicConstant，指定帧所属步骤的域。可能的值为 TIME、FREQUENCY 和 MODAL。

*frequency*

一个 Float，指定频率。此成员仅在 *domain*=FREQUENCY 或 [Step](pt01ch49pyo01.md) 对象的 *procedureType* 成员="FREQUENCY" 时有效。默认值为 0.0。

*mode*

一个整数，指定特征模态。此成员仅在 *domain*=MODAL 时有效。

*associatedFrame*

一个 OdbFrame 对象，指定与此循环对称模式对应的实部或虚部数据。

*fieldOutputs*

[FieldOutput](pt01ch34pyo06.md) 对象仓库，指定 *fieldOutputs* 仓库的键是表示输出变量的字符串。

*loadCase*

一个 [OdbLoadCase](pt01ch34pyo16.md) 对象，指定帧的负载情况。
