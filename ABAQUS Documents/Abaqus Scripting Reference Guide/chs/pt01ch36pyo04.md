# 36.4 DesignResponse 对象

DesignResponse 对象是其他 DesignResponse 对象的抽象基类型。DesponseResponse 对象没有显式构造函数。DesignResponse 对象的方法和成员对所有从 DesignResponse 派生的对象都是通用的。

**访问**

```
import optimization
mdb.models[*name*].optimizationTasks[*name*].designResponses[*name*]
```

### 36.4.1 成员

DesignResponse 对象具有以下成员：

*name*

一个字符串，指定设计响应仓库键。
