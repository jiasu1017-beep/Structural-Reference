# 13.1 Constraint 对象

Constraint 对象是其他约束对象的抽象基类型。Constraint 对象没有显式构造函数。Constraint 对象的成员是所有派生自 Constraint 的对象共有的。

**访问权限**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.1.1 resume()

此方法恢复先前被抑制的约束。

**参数**

无。

**返回值**

无。

**异常**

无。

### 13.1.2 suppress()

此方法抑制约束。

**参数**

无。

**返回值**

无。

**异常**

无。

### 13.1.3 delete(...)

此方法允许您删除现有约束。

**必需参数**

*indices*

整数序列，指定要删除的每个约束的索引。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 13.1.4 成员

Constraint 对象具有以下成员：

*name*

字符串，指定约束存储库键。

*suppressed*

布尔值，指定约束是否被抑制。默认值为 OFF。

