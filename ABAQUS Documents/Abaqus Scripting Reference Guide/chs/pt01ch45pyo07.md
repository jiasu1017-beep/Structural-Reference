# 45.7 Stringer 对象

Stringer 对象存储在实体上创建的加强筋增强信息。

**访问**

```
import part
mdb.models[*name*].parts[*name*].stringers[*name*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.stringers[*name*]
mdb.models[*name*].rootAssembly.instances[*name*].stringers[*name*]
mdb.models[*name*].rootAssembly.stringers[*name*]
```

### 45.7.1 Stringer(...)

此方法从模型数据库中的对象序列创建加强筋。至少需要指定一个可选参数。

**Path**

```
mdb.models[*name*].parts[*name*].Stringer
```

**必需参数**

*name*

 String，指定存储库键。默认值为空字符串。

**可选参数**

*edges*

 Edge 对象序列，指定要创建加强筋的边缘。适用于三维和二维零件。

*elementEdges*

 MeshEdge 对象序列，指定要创建加强筋的网格边缘。适用于三维和二维零件。

**返回值**

Stringer 对象。

**异常**

InvalidNameError。

### 45.7.2 EditStringer(...)

此方法修改所选加强筋的基础实体。至少需要指定一个可选参数。

**Path**

```
mdb.models[*name*].parts[*name*].EditStringer
```

**必需参数**

*name*

 String，指定存储库键。默认值为空字符串。

**可选参数**

*edges*

 Edge 对象序列，指定要创建加强筋的边缘。适用于三维和二维零件。

*elementEdges*

 MeshEdge 对象序列，指定要创建加强筋的网格边缘。适用于三维和二维零件。

**返回值**

Stringer 对象。

**异常**

InvalidNameError。

### 45.7.3 成员

Stringer 对象具有以下成员：

*elements*

 [MeshElementArray](pt01ch31pyo05.md) 对象。

*edges*

 [EdgeArray](pt01ch07pyo03.md) 对象。

