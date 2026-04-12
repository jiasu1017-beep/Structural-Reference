# 39.2 CurrentProbeValues 对象

CurrentProbeValues 对象没有构造函数。导入 Visualization 模块时会创建 CurrentProbeValues 对象。

**访问**

```
import visualization
session.currentProbeValues
```

### 39.2.1 成员

CurrentProbeValues 对象具有以下成员：

*values*

 Float 元组，指定探测时获得的值。当用户移动鼠标到被探测的对象上时，这些值会不断更新。

