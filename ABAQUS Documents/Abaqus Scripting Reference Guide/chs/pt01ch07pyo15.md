# 7.15 Vertex 对象

顶点是几何的点区域。

**访问**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].vertices[*i*]
mdb.models[*name*].parts[*name*].allSets[*name*].vertices[*i*]
mdb.models[*name*].parts[*name*].sets[*name*].vertices[*i*]
mdb.models[*name*].parts[*name*].vertices[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].vertices[*i*]
mdb.models[*name*].rootAssembly.allinstances.vertices[*i*]
mdb.models[*name*].rootAssembly.allInternalSets[*name*].vertices[*i*]
mdb.models[*name*].rootAssembly.allSets[*name*].vertices[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].vertices[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].vertices[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].vertices[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].vertices[*i*]
mdb.models[*name*].rootAssembly.sets[*name*].vertices[*i*]
mdb.models[*name*].rootAssembly.vertices[*i*]
```

### 7.15.1 getEdges()

此方法返回一个由共享该顶点的边缘 ID 组成的序列。

**参数**

无。

**返回值**

一个整数元组。

**异常**

无。

### 7.15.2 getNodes()

此方法返回与顶点关联的节点对象数组。

**参数**

无。

**返回值**

一个 [MeshNodeArray](pt01ch31pyo09.md) 对象，即 [MeshNode](pt01ch31pyo09.md) 对象的序列。

**异常**

无。

### 7.15.3 getElements()

此方法返回与顶点关联的元素对象数组。

**参数**

无。

**返回值**

一个 [MeshElementArray](pt01ch31pyo05.md) 对象，即 [MeshElement](pt01ch31pyo05.md) 对象的序列。

**异常**

无。

### 7.15.4 成员

Vertex 对象具有以下成员：

*index*

一个 Int，指定 Vertex 在 VertexArray 中的索引。

*isReferenceRep*

一个 Boolean，指定顶点是否属于零件或实例的参考表示。

*pointOn*

一个 Float 元组，指定顶点的 *X*-、*Y*- 和 *Z*- 坐标。

*featureName*

一个 Float 元组，指定创建此顶点的特征名称。

*instanceName*

一个 Float 元组，指定此顶点的零件实例名称（如果适用）。
