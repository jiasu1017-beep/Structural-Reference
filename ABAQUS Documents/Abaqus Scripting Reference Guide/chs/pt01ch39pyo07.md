# 39.7 SelectedProbeValues 对象

SelectedProbeValues 对象没有构造函数。导入 Visualization 模块时会创建 SelectedProbeValues 对象。

**访问**

```
import visualization
session.selectedProbeValues
```

### 39.7.1 成员

SelectedProbeValues 对象具有以下成员：

*length*

 Int，指定 *values* 成员的长度。

*fieldOutputAvailable*

 Boolean，指定是否已选择任何探测值（这是写入文件前的必要条件）。

*values*

 Float 元组的元组，指定选定的探测值。

*lastValues*

 Float 元组，指定 *values* 成员的最后一个序列。

