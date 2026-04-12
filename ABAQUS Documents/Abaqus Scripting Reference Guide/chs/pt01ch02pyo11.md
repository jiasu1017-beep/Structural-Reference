# 2.11 RemeshingRule 对象





RemeshingRule 对象控制模型指定区域的自适应重网格调整大小和写入输出数据库的误差指示器。

**访问**

```
import mesh
mdb.models[*name*].remeshingRules[*name*]
```

### 2.11.1 RemeshingRule(...)

此方法创建一个 RemeshingRule 对象。

**路径**

```
mdb.models[*name*].RemeshingRule
```

**必需参数**

*name*

一个 String，指定对象名称。

*stepName*

一个 String，指定此规则进行调整大小发生的步骤名称。

*variables*

一个 String 序列，指定 Abaqus 将用作误差指示器的输出请求变量。

**可选参数**

*description*

一个 String，指定此规则的描述性字符串。默认值为空字符串。

*region*

SymbolicConstant MODEL 或一个 [Region](pt01ch45pyo03.md) 对象，指定 Abaqus 将重网格划分并生成输出的区域。SymbolicConstant MODEL 表示整个适用模型。默认值为 MODEL。

*sizingMethod*

一个 SymbolicConstant，指定计算新网格大小的方法。SymbolicConstant DEFAULT 表示 Abaqus 将对每个单独变量使用默认计算方法。可能的值为 DEFAULT、UNIFORM_ERROR 和 MINIMUM_MAXIMUM。默认值为 DEFAULT。

*errorTarget*

一个 Float，指定区域中每个变量的目标误差百分比。值为 0.0 表示 Abaqus 将对该区域使用自动误差目标缩减。当 *sizingMethod*=UNIFORM_ERROR 时使用 *errorTarget* 参数。默认值为 0.0。

*maxSolutionErrorTarget*

一个 Float，指定区域中最大解值位置的目标误差百分比。值为 0.0 表示 Abaqus 将对该区域使用自动误差目标缩减。当 *sizingMethod*=MINIMUM_MAXIMUM 时使用 *maxSolutionErrorTarget* 参数。默认值为 0.0。

*minSolutionErrorTarget*

一个 Float，指定区域中最小解值位置的目标误差百分比。值为 0.0 表示 Abaqus 将对该区域使用自动误差目标缩减。当 *sizingMethod*=MINIMUM_MAXIMUM 时使用 *minSolutionErrorTarget* 参数。默认值为 0.0。

*meshBias*

一个 Int，指定 Abaqus 将向区域中最大解值位置偏置网格的程度。值越高，网格越偏向最大解值位置。当 *sizingMethod*=MINIMUM_MAXIMUM 时使用 *meshBias* 参数。默认值为 0.0。

*minElementSize*

一个 Float，指定任何单个元素的最小尺寸。默认值为 0.0。

*maxElementSize*

一个 Float，指定任何单个元素的最大尺寸。默认值为 0.0。

*outputFrequency*

一个 SymbolicConstant，指定将误差指示器保存到输出数据库文件（`.odb`）的频率。可能的值为 LAST_INCREMENT 和 ALL_INCREMENTS。默认值为 LAST_INCREMENT。

*specifyMinSize*

一个 Boolean，指定是使用用户提供的最小元素尺寸还是计算特征最小元素尺寸。默认值为 OFF。

*specifyMaxSize*

一个 Boolean，指定是使用用户提供的最大元素尺寸还是计算特征最大元素尺寸。默认值为 ON。

*coarseningFactor*

一个 SymbolicConstant 或 Int，指定从一次重网格迭代到下一次元素生长的上限指示。可能的值为 DEFAULT_LIMIT 和 NOT_ALLOWED。默认值为 DEFAULT_LIMIT。

*refinementFactor*

一个 SymbolicConstant 或 Int，指定从一次重网格迭代到下一次元素收缩的上限指示。可能的值为 DEFAULT_LIMIT 和 NOT_ALLOWED。默认值为 DEFAULT_LIMIT。

*elementCountLimit*

`None` 或一个 Int，指定重网格划分期间将创建的元素的大致数量限制。使用 `None` 表示没有上限。默认值为 `None`。

**返回值**

一个 RemeshingRule 对象。

**异常**

AbaqusException。

### 2.11.2 resume()

此方法恢复之前抑制的重网格规则。

**参数**

无。

**返回值**

无

**异常**

无。

### 2.11.3 suppress()

此方法抑制重网格规则。Abaqus 不会对被抑制规则所在区域进行重网格划分。

**参数**

无。

**返回值**

无

**异常**

无。

### 2.11.4 setValues(...)

此方法修改 RemeshingRule 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [RemeshingRule](pt01ch02pyo11.md#ker-remeshingrule-remeshingrule-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

### 2.11.5 成员

RemeshingRule 对象具有与 [RemeshingRule](pt01ch02pyo11.md#ker-remeshingrule-remeshingrule-pyc) 方法参数相同名称和描述的成员。

此外，RemeshingRule 对象可以具有以下成员：

*suppressed*

一个 Boolean，指定重网格规则是否被抑制。如果您抑制某个规则，则不会对该重网格规则区域进行重网格划分。默认值为 OFF。




