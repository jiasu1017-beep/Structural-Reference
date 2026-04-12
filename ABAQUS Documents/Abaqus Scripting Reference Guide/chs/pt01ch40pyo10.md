# 40.10 OdbDataElementSet 对象

OdbDataElementSet 对象存储单元集数据。

**访问**

```
import visualization
session.odbData[*name*].elementSets[*i*]
```

### 40.10.1 成员

OdbDataElementSet 对象具有以下成员：

*name*

 String，指定集合名称。此属性为只读。

*elements*

字符串到 Int 元组 Dictionary 的 Dictionary，指定集合中的单元。此属性为只读。

