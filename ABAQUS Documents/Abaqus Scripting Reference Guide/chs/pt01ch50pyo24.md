# 50.25 SubstructureGenerateModes 对象

SubstructureGenerateModes 对象用于定义在模态动力学分析中使用的模态。

**访问**

```
import step
mdb.models[*name*].steps[*name*].modeRange[*i*]
```

### 50.25.1 成员

SubstructureGenerateModes 对象具有以下成员：

*start*

一个 Int，指定范围最低模态的模态号。

*end*

一个 Int，指定范围最高模态的模态号。

*increment*

一个 Int，指定用于从最低模态到最高模态定义中间模态号的增量。
