# 50.14 RayleighDampingComponent 对象

RayleighDampingComponent 对象用于定义一系列模态的 Rayleigh 阻尼。

**访问**

```
import step
mdb.models[*name*].steps[*name*].rayleighDamping.components[*i*]
```

### 50.14.1 成员

RayleighDampingComponent 对象具有以下成员：

*start*

一个 Int，指定范围最低模态的模态号。

*end*

一个 Int，指定范围最高模态的模态号。

*alpha*

一个 Float，指定质量比例阻尼 ![](../graphics/ker_eqn00423.gif)。

*beta*

一个 Float，指定刚度比例阻尼 ![](../graphics/ker_eqn00424.gif)。
