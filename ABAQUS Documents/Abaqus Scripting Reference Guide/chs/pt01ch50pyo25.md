# 50.23 StructuralDampingComponent 对象

StructuralDampingComponent 对象用于定义一系列模态的结构阻尼。

**访问**

```
import step
mdb.models[*name*].steps[*name*].structuralDamping.components[*i*]
```

### 50.23.1 成员

StructuralDampingComponent 对象具有以下成员：

*start*

一个 Int，指定范围最低模态的模态号。

*end*

一个 Int，指定范围最高模态的模态号。

*factor*

一个 Float，指定阻尼因子 ![](../graphics/ker_eqn00234.gif)。
