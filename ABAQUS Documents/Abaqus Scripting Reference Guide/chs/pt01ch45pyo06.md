# 45.6 Skin 对象

Skin 对象存储在实体上创建的皮肤增强信息。

**访问**

```
import part
mdb.models[*name*].parts[*name*].skins[*name*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.skins[*name*]
mdb.models[*name*].rootAssembly.instances[*name*].skins[*name*]
mdb.models[*name*].rootAssembly.skins[*name*]
```

### 45.6.1 Skin(...)

此方法从模型数据库中的对象序列创建皮肤。至少需要指定一个可选参数。

**Path**

```
mdb.models[*name*].parts[*name*].Skin
```

**必需参数**

*name*

 String，指定存储库键。默认值为空字符串。

**可选参数**

*faces*

 Face 对象序列，指定要创建皮肤的面。适用于三维和二维零件。

*edges*

 Edge 对象序列，指定要创建皮肤的边缘。适用于轴对称零件。

*elementFaces*

 MeshFace 对象序列，指定要创建皮肤的网格面。适用于三维和二维零件。

*elementEdges*

 MeshEdge 对象序列，指定要创建皮肤的网格边缘。适用于轴对称零件。

**返回值**

Skin 对象。

**异常**

InvalidNameError。

### 45.6.2 EditSkin(...)

此方法修改所选皮肤的基础实体。至少需要指定一个可选参数。

**Path**

```
mdb.models[*name*].parts[*name*].EditSkin
```

**必需参数**

*name*

 String，指定存储库键。默认值为空字符串。

**可选参数**

*faces*

 Face 对象序列，指定要创建皮肤的面。适用于三维和二维零件。

*edges*

 Edge 对象序列，指定要创建皮肤的边缘。适用于轴对称零件。

*elementFaces*

 MeshFace 对象序列，指定要创建皮肤的网格面。适用于三维和二维零件。

*elementEdges*

 MeshEdge 对象序列，指定要创建皮肤的网格边缘。适用于轴对称零件。

**返回值**

Skin 对象。

**异常**

InvalidNameError。

### 45.6.3 成员

Skin 对象具有以下成员：

*elements*

 [MeshElementArray](pt01ch31pyo05.md) 对象。

*edges*

 [EdgeArray](pt01ch07pyo03.md) 对象。

*faces*

 [FaceArray](pt01ch07pyo05.md) 对象。

