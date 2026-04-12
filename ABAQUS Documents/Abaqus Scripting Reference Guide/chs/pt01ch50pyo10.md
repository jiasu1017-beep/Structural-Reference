# 50.10 RandomResponseFrequency 对象

RandomResponseFrequency 是一个用于定义模态范围频率的对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*].freq[*i*]
```

### 50.10.1 成员

RandomResponseFrequency 对象具有以下成员：

*lower*

一个 Float，指定频率范围的下限（以每时间周期计）。

*upper*

一个 Float，指定频率范围的上限（以每时间周期计）。

*nCalcs*

一个 Int，指定在特征频率之间应计算响应的点数。

*bias*

一个 Float，指定偏置参数。
