# 50.19 SteadyStateSubspaceFrequency 对象

SteadyStateSubspaceFrequency 是一个用于定义模态范围频率的对象。

**访问**

```
import step
mdb.models[*name*].steps[*name*].frequencyRange[*i*]
```

### 50.19.1 成员

SteadyStateSubspaceFrequency 对象具有以下成员：

*lower*

一个 Float，指定频率范围的下限或单个频率（以周期/时间计）。

*upper*

一个 Float，指定频率范围的上限（以周期/时间计）。

*nPoints*

一个 Int，指定应给出结果的频率范围内的点数。

*bias*

一个 Float，指定偏置参数。当请求在四个或更多频率点给出结果时，Abaqus 会将结果偏向间隔的端点，以获得更好的分辨率。默认值为 3.0。
