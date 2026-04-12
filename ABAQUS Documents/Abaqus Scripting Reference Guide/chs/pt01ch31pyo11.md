# 31.12 MeshEdgeArray 对象

MeshEdgeArray 是 [MeshEdge](pt01ch31pyo04.md) 对象的序列。

**访问**

```
import part
mdb.models[*name*].parts[*name*].elementEdges
import assembly
mdb.models[*name*].rootAssembly.allinstances.elementEdges
mdb.models[*name*].rootAssembly.instances[*name*].elementEdges
```

### 31.12.1 MeshEdgeArray(...)

此方法创建一个 MeshEdgeArray 对象。

**路径**

```
mesh.MeshEdgeArray
```

**必要参数**

*edges*

[MeshEdge](pt01ch31pyo04.md) 对象列表。

**可选参数**

无。

**返回值**

MeshEdgeArray 对象。

**异常**

无。

### 31.12.2 getSequenceFromMask(...)

此方法返回使用指定 *mask* 标识的 MeshEdgeArray 中的对象。当涉及大量对象时，此方法效率很高。

**必要参数**

*mask*

一个字符串，指定对象或多个对象。

**可选参数**

无。

**返回值**

MeshEdgeArray 对象。

**异常**

如果结果序列为空，则引发异常。

```
Error: The mask results in an empty sequence
```

### 31.12.3 getMask()

此方法返回指定对象或多个对象的字符串。

**参数**

无。

**返回值**

一个字符串，指定对象或多个对象。

**异常**

无。

### 31.12.4 成员

MeshEdgeArray 对象没有成员。
