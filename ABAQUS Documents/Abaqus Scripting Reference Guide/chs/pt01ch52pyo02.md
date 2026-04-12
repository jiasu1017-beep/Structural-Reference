# 52.2 textRepr 模块







`textRepr` Python 模块包含用于打印 Abaqus 对象以及将 `str()` 函数的输出转换为格式化字符串的函数，该字符串为 Python 对象递归列表中的每个对象都进行了缩进。

**访问**

```
import textRepr
```

### 52.2.1 getIndentedRepr(...)

该方法返回一个 String，其中每个括号级别都进行了缩进。

**必需参数**

*object*

要处理的 Python 对象。（Python 对象可以是 Abaqus 对象。）此参数也可以是从 str(*object*) 获取的 Python 对象的 String 表示形式。

**可选参数**

*maxRecursionDepth*

一个 Int，指定对象被打印的最大深度，SymbolicConstant UNLIMITED 或 `None`。`None` 值意味着将使用 TextReprOptions 对象中的当前设置。如果 *object* 不是 Abaqus 对象，则 *maxRecursionDepth* 没有效果。默认值为 `None`。

设置 *maxRecursionDepth*=UNLIMITED 时应小心，因为结果输出可能非常大。要限制输出，应将 *maxElementsInSequence* 设置为较小的数字。

*maxElementsInSequence*

一个 Int，指定要返回的序列元素的最大数量，或 SymbolicConstant UNLIMITED。初始值为 100。打印完最大数量的元素后，剩余元素用字符串 '...' 表示。

*significantDigits*

一个 Int，指定输出中 Float 的有效数字位数。可能的值为 0 ![](../graphics/ker_eqn00048.gif) *significantDigits* ![](../graphics/ker_eqn00425.gif) 15。默认值为 6。

**返回值**

一个 String。

**异常**

None。

### 52.2.2 getPaths(...)

该方法处理参数并解释其结构。然后返回一个 String，其中包含找到的所有子对象的路径。

**必需参数**

*object*

要处理的 Python 对象。（Python 对象可以是 Abaqus 对象。）此参数也可以是 Python 对象的 String 表示形式。

**可选参数**

*maxRecursionDepth*

一个 Int，指定对象被打印的最大深度，SymbolicConstant UNLIMITED 或 `None`。`None` 值意味着将使用 TextReprOptions 对象中的当前设置。如果 *object* 不是 Abaqus 对象，则 *maxRecursionDepth* 没有效果。默认值为 `None`。

设置 *maxRecursionDepth*=UNLIMITED 时应小心，因为结果输出可能非常大。要限制输出，应将 *maxElementsInSequence* 设置为较小的数字。

*maxElementsInSequence*

一个 Int，指定要返回的序列元素的最大数量，或 SymbolicConstant UNLIMITED。初始值为 100。打印完最大数量的元素后，剩余元素用字符串 '...' 表示。

*pathRoot*

一个 String，指定路径的根。此 String 被添加到找到的每个路径前面。默认值为 `None`，这意味着将使用 *object* 的路径，除非 *object* 是一个 String。

**返回值**

一个 String。

**异常**

None。

### 52.2.3 getTypes(...)

该方法处理参数，解释其结构，并返回一个 String，其中包含对象中所有对象类型，格式为 '*TypeName* *Path*'。

**必需参数**

*object*

一个 Abaqus 对象。

**可选参数**

*maxRecursionDepth*

一个 Int，指定对象被打印的最大深度，SymbolicConstant UNLIMITED 或 `None`。`None` 值意味着将使用 TextReprOptions 对象中的当前设置。默认值为 `None`。

设置 *maxRecursionDepth*=UNLIMITED 时应小心，因为结果输出可能非常大。要限制输出，应将 *maxElementsInSequence* 设置为较小的数字。

*maxElementsInSequence*

一个 Int，指定要返回的序列元素的最大数量，或 SymbolicConstant UNLIMITED。初始值为 100。打印完最大数量的元素后，剩余元素用字符串 '...' 表示。

*pathRoot*

一个 String，指定路径的根。此 String 被添加到找到的每个路径前面。默认值为 `None`，这意味着将使用 *object* 的路径，除非 *object* 是一个 String。

**返回值**

一个 String。

**异常**

None。

### 52.2.4 prettyPrint(...)

该方法打印对象的格式化版本。`prettyPrint` 函数使用 `getIndentedRepr` 来格式化 String 表示，但不保存 `getIndentedRepr` 的完整文本输出。因此，此函数可用于 `getIndentedRepr` 会耗尽内存的情况。

**必需参数**

*object*

一个 Abaqus 对象。

**可选参数**

*maxRecursionDepth*

一个 Int，指定对象被打印的最大深度，SymbolicConstant UNLIMITED 或 `None`。`None` 值意味着将使用 TextReprOptions 对象中的当前设置。默认值为 `None`。

设置 *maxRecursionDepth*=UNLIMITED 时应小心，因为结果输出可能非常大。要限制输出，应将 *maxElementsInSequence* 设置为较小的数字。

*maxElementsInSequence*

一个 Int，指定要返回的序列元素的最大数量，或 SymbolicConstant UNLIMITED。初始值为 100。打印完最大数量的元素后，剩余元素用字符串 '...' 表示。

*significantDigits*

一个 Int，指定输出中 Float 的有效数字位数。可能的值为 0 ![](../graphics/ker_eqn00048.gif) *significantDigits* ![](../graphics/ker_eqn00425.gif) 15。默认值为 6。

**返回值**

None

**异常**

None。

### 52.2.5 printPaths(...)

该方法打印 *object* 参数及其成员的对象路径，具体取决于 *maxRecursionDepth* 参数。`printPaths` 函数使用 `getPaths` 打印 *object* 中每个子对象的路径列表。

**必需参数**

*object*

一个 Abaqus 对象。此参数也可以是从 str(*object*) 获取的 Abaqus 对象的 String 表示形式。

**可选参数**

*maxRecursionDepth*

一个 Int，指定对象被打印的最大深度，SymbolicConstant UNLIMITED 或 `None`。`None` 值意味着将使用 TextReprOptions 对象中的当前设置。默认值为 `None`。

设置 *maxRecursionDepth*=UNLIMITED 时应小心，因为结果输出可能非常大。要限制输出，应将 *maxElementsInSequence* 设置为较小的数字。

*maxElementsInSequence*

一个 Int，指定要返回的序列元素的最大数量，或 SymbolicConstant UNLIMITED。初始值为 100。打印完最大数量的元素后，剩余元素用字符串 '...' 表示。

*pathRoot*

一个 String，指定要打印的路径的根。此 String 被添加到找到的每个路径前面。默认值为 `None`，这意味着将使用 *object* 的路径。

**返回值**

None

**异常**

None。

### 52.2.6 printTypes(...)

该方法打印对象类型。`printTypes` 函数使用 `getTypes` 打印 *object* 中所有对象类型的列表。

**必需参数**

*object*

一个 Abaqus 对象。

**可选参数**

*maxRecursionDepth*

一个 Int，指定对象被打印的最大深度，SymbolicConstant UNLIMITED 或 `None`。`None` 值意味着将使用 TextReprOptions 对象中的当前设置。默认值为 `None`。

设置 *maxRecursionDepth*=UNLIMITED 时应小心，因为结果输出可能非常大。要限制输出，应将 *maxElementsInSequence* 设置为较小的数字。

*maxElementsInSequence*

一个 Int，指定要返回的序列元素的最大数量，或 SymbolicConstant UNLIMITED。初始值为 100。打印完最大数量的元素后，剩余元素用字符串 '...' 表示。

*pathRoot*

一个 String，指定要打印的路径的根。此 String 被添加到找到的每个路径前面。默认值为 `None`，这意味着将使用 *object* 的路径。

**返回值**

None

**异常**

None。

