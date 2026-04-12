# 7.10 IgnoredVertexArray 对象

IgnoredVertexArray 是 [IgnoredVertex](pt01ch07pyo09.md) 对象的序列。如果零件被修改，则必须为该零件更新 IgnoredVertexArray。

**访问**

```
import part
mdb.models[*name*].parts[*name*].ignoredVertices
import assembly
mdb.models[*name*].rootAssembly.allinstances.ignoredVertices
mdb.models[*name*].rootAssembly.instances[*name*].ignoredVertices
```

### 7.10.1 findAt(...)

此方法返回位于给定坐标处的 IgnoredVertexArray 中的对象。

`findAt` 最初使用 ACIS 容差 1E-6。因此，`findAt` 返回任意点指定处或距离任意点小于 1E-6 的任何 [IgnoredVertex](pt01ch07pyo09.md)。如果未找到任何内容，`findAt` 使用不精确几何的容差（仅适用于不精确几何实体）。

`findAt` 将始终尝试在零件或装配实例中的所有被忽略顶点中查找对象，而不会将自己限制为子集，即使 IgnoredVertexArray 表示这样的子集。

**必需参数**

*coordinates*

一个 Float 序列，指定要查找的对象的 *X*-、*Y*- 和 *Z*- 坐标。

`findAt` 根据输入类型返回 [IgnoredVertex](pt01ch07pyo09.md) 对象或 [IgnoredVertex](pt01ch07pyo09.md) 对象序列。
- 如果 *coordinates* 是 Float 序列，则 `findAt` 返回该点的 [IgnoredVertex](pt01ch07pyo09.md) 对象。
- 如果省略 *coordinates* 关键字参数，则 `findAt` 接受以下格式的 float 序列序列作为参数：``` verts = v.findAt(((20.19686, -169.513997, 27.798593), ), ((19.657627, -167.295749, 27.056402), ), ((18.274129, -157.144741, 25.15218), )) ```

**可选参数**

*printWarning*

一个 Boolean，指定如果在该位置未找到实体，是否向 CLI 打印消息。默认值为 True。

**返回值**

一个 [IgnoredVertex](pt01ch07pyo09.md) 对象或 [IgnoredVertex](pt01ch07pyo09.md) 对象序列。

**异常**

无。

### 7.10.2 getSequenceFromMask(...)

此方法返回使用指定 *mask* 标识的 IgnoredVertexArray 中的对象。当 [JournalOptions](pt01ch47pyo06.md) 设置为 COMPRESSEDINDEX 时，会生成此命令。当涉及大量对象时，此方法非常高效。

**必需参数**

*mask*

一个 String，指定对象或对象。

**可选参数**

无。

**返回值**

一个 [IgnoredVertex](pt01ch07pyo09.md) 对象或 [IgnoredVertex](pt01ch07pyo09.md) 对象序列。

**异常**

无。

### 7.10.3 getMask()

此方法返回一个字符串，指定对象或对象。

**参数**

无。

**返回值**

一个 String，指定对象或对象。

**异常**

无。

### 7.10.4 getClosest(...)

此方法返回 IgnoredVertexArray 中离给定点集最近的对象或对象，给定点不必位于 IgnoredVertexArray 中的顶点上。

**必需参数**

*coordinates*

一个 float 序列的序列，其中每个 float 序列描述一个点的 *X*-、*Y*- 和 *Z*- 坐标。

```
r=e.getClosest(coordinates=((20.0,20.0,10.0),(-1.0, -15.0, 15),))
```

```
r.keys()
```

```
[0, 1]
```

```
r[0]
```

```
(mdb.models['Model-1'].parts['Part-1'].ignoredVertices[3],
                                 (15.7090625762939, 20.0, 10.0))
```

**可选参数**

*searchTolerance*

一个 double，指定最近对象必须位于的距离内。默认值为父零件/实例大小的一半。

**返回值**

此方法返回一个字典对象。字典的键是 *coordinates* 中指定输入点在元组中的位置，从索引 0 开始。如果找到最近的 [IgnoredVertex](pt01ch07pyo09.md)，则值是一个包含两个对象的序列。序列中的第一个对象是一个 [IgnoredVertex](pt01ch07pyo09.md)，靠近键所指的输入点。序列中的第二个对象是一个 float 序列，指定 [IgnoredVertex](pt01ch07pyo09.md) 上到给定点的最近点的 *X*-、*Y*- 和 *Z*- 位置。请参阅上面的程序列表。

**异常**

如果结果序列为空，则抛出异常。

```
Error: The mask results in an empty sequence
```

### 7.10.5 成员

IgnoredVertexArray 对象没有成员。
