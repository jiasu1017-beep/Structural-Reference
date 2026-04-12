# 50.2 CompositeDampingComponent 对象

CompositeDampingComponent 对象用于定义一系列模态的复合阻尼。

**访问**

```
import step
mdb.models[*name*].steps[*name*].compositeDamping.components[*i*]
```

### 50.2.1 成员

CompositeDampingComponent 对象具有以下成员：

*start*

一个 Int，指定范围最低模态的模态号。

*end*

一个 Int，指定范围最高模态的模态号。
