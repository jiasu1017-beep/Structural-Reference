# 40.15 OdbDataSection 对象

OdbDataSection 对象存储截面数据。

**访问**

```
import visualization
session.odbData[*name*].sections[*i*]
```

### 40.15.1 成员

OdbDataSection 对象具有以下成员：

*name*

 String，指定集合名称。此属性为只读。

*elements*

字符串到 Int 元组 Dictionary 的 Dictionary，指定集合中的单元。此属性为只读。

