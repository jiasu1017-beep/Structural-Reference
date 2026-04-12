# 40.17 OdbDataSurfaceSet 对象

OdbDataSurfaceSet 对象存储曲面集数据。

**访问**

```
import visualization
session.odbData[*name*].surfaceSets[*i*]
```

### 40.17.1 成员

OdbDataSurfaceSet 对象具有以下成员：

*name*

 String，指定集合名称。此属性为只读。

*elements*

字符串到 Int 元组 Dictionary 的 Dictionary，指定集合中的单元。此属性为只读。

*facets*

字符串到 Int 元组 Dictionary 的 Dictionary，指定与 *elements* 对应的面。此属性为只读。

