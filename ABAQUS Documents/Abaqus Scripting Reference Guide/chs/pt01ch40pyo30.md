# 40.30 MdbDataStep 对象

MdbDataStep 对象。它对应于 cae 模型中同名的步骤。

**访问**

```
import visualization
session.mdbData[*name*].steps[*i*]
```

### 40.30.1 成员

MdbDataStep 对象具有以下成员：

*frames*

 [MdbDataFrameArray](pt01ch40pyo28.md) 对象，指定帧列表。此列表为只读。步骤中只有一个帧。

