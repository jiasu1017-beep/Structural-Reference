# 14.3 RegisteredDictionary 对象

此类允许您创建一个可从 GUI 查询的字典，并能够在字典内容更改时通知 GUI。RegisteredDictionary 的键必须是字符串或整数。

RegisteredDictionary 对象派生自 [CommandRegister](pt01ch14pyo01.md) 对象。

**访问权限**

```
import customKernel
```

### 14.3.1 RegisteredDictionary()

此方法创建一个 RegisteredDictionary 对象。

**路径**

```
customKernel.RegisteredDictionary
```

**返回值**

RegisteredDictionary 对象。

**异常**

无。

### 14.3.2 方法()

RegisteredDictionary 对象支持与 Python 字典相同的方法。此外，RegisteredDictionary 对象支持 `changeKey` 方法。

**参数**

无。

**返回值**

无。

**异常**

无。

### 14.3.3 changeKey(...)

此方法更改字典中键的名称。

**必需参数**

*fromName*

字符串或整数，指定要更改的键的名称。

*toName*

字符串或整数，指定键的新名称。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 14.3.4 成员

RegisteredDictionary 对象没有成员。

