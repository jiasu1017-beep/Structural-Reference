# 50.24 SubstructureGenerateFrequency 对象

SubstructureGenerateFrequency 对象用于定义在模态动力学分析中使用的模态。这些模态从指定的频率范围（包括频率边界）中选择。

**访问**

```
import step
mdb.models[*name*].steps[*name*].frequencyRange[*i*]
```

### 50.24.1 成员

SubstructureGenerateFrequency 对象具有以下成员：

*lower*

一个 Float，指定频率范围的下限（以周期/时间计）。

*upper*

一个 Float，指定频率范围的上限（以周期/时间计）。
