# 50.7 DirectDampingComponent 对象

DirectDampingComponent 对象用于定义一系列模态的直接阻尼。

**访问**

```
import step
mdb.models[*name*].steps[*name*].directDamping.components[*i*]
```

### 50.7.1 成员

DirectDampingComponent 对象具有以下成员：

*start*

一个 Int，指定范围最低模态的模态号。

*end*

一个 Int，指定范围最高模态的模态号。

*fraction*

一个 Float，指定临界阻尼比。
