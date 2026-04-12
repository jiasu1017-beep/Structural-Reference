# 50.22 StructuralDampingByFrequencyComponent 对象

StructuralDampingByFrequencyComponent 对象用于定义一系列频率的结构阻尼。

**访问**

```
import step
mdb.models[*name*].steps[*name*].structuralDampingByFrequency\
.components[*i*]
```

### 50.22.1 成员

StructuralDampingByFrequencyComponent 对象具有以下成员：

*frequency*

一个 Float，指定频率值（周期/时间）。

*factor*

一个 Float，指定阻尼因子 ![](../graphics/ker_eqn00234.gif)。
