# 34.26 ScratchOdb 对象

临时输出数据库与打开的输出数据库关联，用于存储会话相关的非持久对象，如 Step、Frame 和 [FieldOutput](pt01ch34pyo06.md) 对象。Abaqus 在 Abaqus/CAE 会话期间需要这些非持久对象时创建临时输出数据库。当关联的输出数据库关闭时，Abaqus 删除临时输出数据库。

**访问**

```
import odbAccess
session.scratchOdbs[*name*]
```

### 34.26.1 ScratchOdb(...)

此方法创建新的 ScratchOdb 对象。

**路径**

```
session.ScratchOdb
```

**必要参数**

*odb*

一个 [Odb](pt01ch34pyo01.md) 对象，指定关联的输出数据库。

**可选参数**

无。

**返回值**

ScratchOdb 对象。

**异常**

无。

### 34.26.2 成员

ScratchOdb 对象没有成员。
