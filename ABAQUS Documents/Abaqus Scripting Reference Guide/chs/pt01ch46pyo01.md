# 46.1 Section 对象

Section 对象定义截面的属性。Section 对象是其他 Section 对象的抽象基类型。Section 对象没有显式构造函数。Section 对象的方法和成员对所有派生对象通用。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.1.1 sectionsFromOdb(...)

此方法通过读取输出数据库创建 Section 对象。新截面被放入 `sections` 存储库。

**Path**

```
mdb.models[*name*].sectionsFromOdb
```

**必需参数**

*fileName*

 String，指定要读取的输出数据库文件的名称（包括 `.odb` 扩展名）。如果该文件位于其他目录，这也可以是输出数据库文件的完整路径。

**可选参数**

无。

**返回值**

Section 对象列表。

**异常**

无。

### 46.1.2 成员

Section 对象具有以下成员：

*name*

 String，指定存储库键。

