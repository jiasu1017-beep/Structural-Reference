# 46.22 SolidSection 对象





SolidSection 对象定义实体截面的属性。SolidSection 对象没有显式构造函数，没有成员，也没有方法。SolidSection 对象是一个抽象基类型。

SolidSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.22.1 成员

SolidSection 对象具有以下成员：

*name*

String，指定存储库键。


