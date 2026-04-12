# 39.4 NodeQuery 对象

NodeQuery 对象指定路径中节点的节点及其坐标。NodeQuery 对象没有构造函数或方法。导入 `visualization` 模块时，Abaqus 会创建 *nodeQuery* 成员。

**访问**

```
import visualization
session.nodeQuery
```

### 39.4.1 成员

NodeQuery 对象具有以下成员：

*nodeId*

 Int，指定最近查询的节点 ID。如果最后一次查询不成功，则 *nodeID*=1。

*nodePos*

 Float 元组，指定最近查询的节点的 *X*、*Y* 和 *Z* 坐标。

