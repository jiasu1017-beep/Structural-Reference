# 31.11 MeshFaceArray 对象

MeshFaceArray 是 [MeshFace](pt01ch31pyo08.md) 对象的序列。

**访问**

```
import part
mdb.models[*name*].parts[*name*].elementFaces
import assembly
mdb.models[*name*].rootAssembly.allinstances.elementFaces
mdb.models[*name*].rootAssembly.instances[*name*].elementFaces
```

### 31.11.1 MeshFaceArray(...)

此方法创建一个 MeshFaceArray 对象。

**路径**

```
mesh.MeshFaceArray
```

**必要参数**

*faces*

[MeshFace](pt01ch31pyo08.md) 对象列表。

**可选参数**

无。

**返回值**

MeshFaceArray 对象。

**异常**

无。

### 31.11.2 getSequenceFromMask(...)

此方法返回使用指定 *mask* 标识的 MeshFaceArray 中的对象。当涉及大量对象时，此方法效率很高。

**必要参数**

*mask*

一个字符串，指定对象或多个对象。

**可选参数**

无。

**返回值**

MeshFaceArray 对象。

**异常**

如果结果序列为空，则引发异常。

```
Error: The mask results in an empty sequence
```

### 31.11.3 getMask()

此方法返回指定对象或多个对象的字符串。

**参数**

无。

**返回值**

一个字符串，指定对象或多个对象。

**异常**

无。

### 31.11.4 成员

MeshFaceArray 对象没有成员。
