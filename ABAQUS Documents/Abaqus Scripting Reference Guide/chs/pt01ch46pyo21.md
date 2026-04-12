# 46.21 ShellSection 对象





ShellSection 对象定义壳截面的属性。ShellSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。ShellSection 对象没有显式构造函数，也没有方法或成员。

ShellSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.21.1 成员

ShellSection 对象可以具有以下成员：

*name*

String，指定存储库键。

*transverseShear*

[TransverseShearShell](pt01ch46pyo25.md) 对象，指定横向剪切刚度属性。


