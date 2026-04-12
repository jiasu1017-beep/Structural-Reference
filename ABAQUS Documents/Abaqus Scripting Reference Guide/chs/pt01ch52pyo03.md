# 52.3 TextReprOptions 对象

TextReprOptions 对象用于配置 Abaqus/CAE 中 Python `str()` 命令的输出。（`str()` 命令被 Python print 函数使用。）TextReprOptions 对象存储各种设置，这些设置决定对象如何在 Python 命令行上打印。

TextReprOptions 对象没有构造函数。当会话启动时，Abaqus 会创建 *textReprOptions* 成员。

**访问**

```
import textRepr
textReprOptions
session.textReprOptions
```

### 52.3.1 setValues(...)

该方法修改 TextReprOptions 对象。

**必需参数**

无。

**可选参数**

*style*

一个 SymbolicConstant，指定文本表示的样式。可能的值为：
- RECURSIVE：返回对象的递归表示。
- SIMPLE：返回一个 String，将对象表示为 'interface object'、'dictionary object' 或 'sequence object'。

初始值为 RECURSIVE。

*maxRecursionDepth*

一个 Int、SymbolicConstant 或 `None`，指定对象被打印的最大深度。可用于深度的值为 Int  ![](../graphics/ker_eqn00426.gif) 0、SymbolicConstant UNLIMITED 或 `None`。`None` 值意味着将使用 TextReprOptions 对象中的当前设置。如果 *object* 不是 Abaqus 对象，则 *maxRecursionDepth* 没有效果。默认值为 `None`。

*maxRecursionString*

一个 String，指定达到最大递归深度时返回的字符串。该字符串可以包含格式说明符 (%s)，它将被对象类型替换。初始值为 '%s object'。

*maxElementsInSequence*

一个 Int 或 SymbolicConstant UNLIMITED，指定要返回的序列元素的最大数量。可取的值是 UNLIMITED 或 Int  ![](../graphics/ker_eqn00060.gif) 0。初始值为 100。打印完最大数量的元素后，剩余元素用字符串 '...' 表示。

**返回值**

无。

**异常**

无。

### 52.3.2 成员

TextReprOptions 对象的成员与 [setValues](pt01ch52pyo03.md#ker-txt-textrepop-setvalues-pyc) 方法的参数具有相同的名称和描述。
