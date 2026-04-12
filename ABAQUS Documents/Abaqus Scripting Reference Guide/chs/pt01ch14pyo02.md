# 14.2 RepositorySupport 对象

`RepositorySupport` 是一个基类，您可以从中派生自己的类，这些类旨在包含自定义存储库。此类的实例可以从 GUI 查询，并能够在实例内容更改时通知 GUI。

RepositorySupport 对象派生自 [CommandRegister](pt01ch14pyo01.md) 对象。

**访问权限**

```
import customKernel
mdb.customData
session.customData
session.odbs[*name*].customData
```

### 14.2.1 RepositorySupport()

此方法创建一个 RepositorySupport 对象。

**路径**

```
customKernel.RepositorySupport
```

**返回值**

RepositorySupport 对象。

**异常**

无。

### 14.2.2 Repository(...)

此方法在类上安装一个存储库。该存储库是 `RegisteredDictionary` 类的实例。关于其方法的详细信息，请参阅 [RegisteredDictionary](pt01ch14pyo03.md)。

存储在存储库中的对象假定有一个名为 *name* 的属性，用于存储在存储库中访问对象的键。name 属性将由 `changeKey` 方法修改。

**必需参数**

*name*

字符串，指定存储库的名称。

*constructors*

构造函数或构造函数序列，指定哪些类将把它们的对象存储在存储库中。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 14.2.3 成员

RepositorySupport 对象没有成员。

