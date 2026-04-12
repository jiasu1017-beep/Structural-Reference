# 50.6 DirectDampingByFrequencyComponent 对象

DirectDampingByFrequencyComponent 对象用于定义一系列频率的直接阻尼。

**访问**

```
import step
mdb.models[*name*].steps[*name*].directDampingByFrequency.components[*i*]
```

### 50.6.1 成员

DirectDampingByFrequencyComponent 对象具有以下成员：

*frequency*

一个 Float，指定频率值（周期/时间）。

*fraction*

一个 Float，指定临界阻尼比。
