# 14.5 RegisteredTuple 对象

此类允许您创建一个元组，该元组可从 GUI 查询，并能够在元组任何成员的内容更改时通知 GUI。

RegisteredTuple 对象派生自 [CommandRegister](pt01ch14pyo01.md) 对象。

**访问权限**

```
import customKernel
```

### 14.5.1 RegisteredTuple(...)

此方法创建一个 RegisteredTuple 对象。

**路径**

```
customKernel.RegisteredTuple
```

**必需参数**

*tuple*

对象元组。这些对象必须派生自 CommandRegister 类。

**可选参数**

无。

**返回值**

RegisteredTuple 对象。

**异常**

无。

### 14.5.2 方法()

RegisteredTuple 对象支持与标准 Python 列表对象相同的方法。

**参数**

无。

**返回值**

无。

**异常**

无。

### 14.5.3 成员

RegisteredTuple 对象没有成员。

