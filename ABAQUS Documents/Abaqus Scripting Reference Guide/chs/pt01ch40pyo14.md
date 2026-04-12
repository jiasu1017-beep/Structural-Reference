# 40.14 OdbDataNodeSet 对象

OdbDataNodeSet 对象存储节点集数据。

**访问**

```
import visualization
session.odbData[*name*].nodeSets[*i*]
```

### 40.14.1 成员

OdbDataNodeSet 对象具有以下成员：

*name*

 String，指定集合名称。此属性为只读。

*nodes*

字符串到 Int 元组 Dictionary 的 Dictionary，指定集合中的节点。此属性为只读。

