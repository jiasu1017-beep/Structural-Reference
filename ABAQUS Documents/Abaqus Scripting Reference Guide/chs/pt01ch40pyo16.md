# 40.16 OdbDataStep 对象

OdbDataStep 对象。

**访问**

```
import visualization
session.odbData[*name*].steps[*i*]
```

### 40.16.1 setValues(...)

此方法修改 OdbDataStep 对象。

**必需参数**

*activateFrames*

 Boolean，指定是否激活步骤中的所有帧。

**可选参数**

*update*

 Boolean，指定是否更新模型。默认值为 ON

**返回值**

无

**异常**

无。

### 40.16.2 成员

OdbDataStep 对象具有以下成员：

*frames*

 [OdbDataFrameArray](pt01ch40pyo11.md) 对象，指定帧列表。此列表为只读。

