# 8.1 Profile 对象

Profile 对象定义梁横截面的几何属性。Profile 是一个抽象基类型。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.1.1 beamProfilesFromOdb(...)

此方法通过读取输出数据库创建 Profile 对象。新的 profile 被放入 `profiles` 存储库中。

**路径**

```
mdb.models[*name*].beamProfilesFromOdb
```

**必需参数**

*fileName*

一个 String，指定要读取的输出数据库文件的名称（包括 `.odb` 扩展名）。如果输出数据库文件位于另一个目录，String 也可以是输出数据库文件的完整路径。

**可选参数**

无。

**返回值**

一个 Profile 对象列表。

**异常**

无。

### 8.1.2 成员

Profile 对象具有以下成员：

*name*

一个 String，指定存储库键。
