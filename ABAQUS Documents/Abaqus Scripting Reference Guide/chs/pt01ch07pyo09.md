# 7.9 IgnoredVertex 对象





IgnoredVertex 对象是由虚拟拓扑特征抽象掉的几何的点区域。

**访问**

```
import part
mdb.models[*name*].parts[*name*].ignoredVertices[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.ignoredVertices[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].ignoredVertices[*i*]
```

### 7.9.1 成员

IgnoredVertex 对象具有以下成员：

*index*

一个 Int，指定 IgnoredVertex 在 IgnoredVertexArray 中的索引。

*pointOn*

一个 Float 元组，指定顶点的 *X*-、*Y*- 和 *Z*- 坐标。




