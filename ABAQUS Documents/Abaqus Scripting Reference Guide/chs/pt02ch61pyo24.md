# 61.24 OdbSet 对象

集对象用于标识模型的区域。

**访问**

```
odb.parts()[*name*].elementSets()[*name*]
odb.parts()[*name*].nodeSets()[*name*]
odb.parts()[*name*].surfaces()[*name*]
odb.rootAssembly().elementSets()[*name*]
odb.rootAssembly().instances()[*name*].elementSets()[*name*]
odb.rootAssembly().instances()[*name*].nodeSets()[*name*]
odb.rootAssembly().instances()[*name*].surfaces()[*name*]
odb.rootAssembly().nodeSets()[*name*]
odb.rootAssembly().surfaces()[*name*]
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elementSets()[*name*]
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodeSets()[*name*]
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.surfaces()[*name*]
```

### 61.24.1 NodeSet(...)

此方法从 [OdbMeshNode](pt02ch61pyo19.md) 对象数组创建节点集（用于部件实例级集）。

**路径**

```
odb.parts()[*name*].NodeSet
```

```
odb.rootAssembly().instances()[*name*].NodeSet
```

**原型**

```
odb_Set&
NodeSet(const odb_String& name,
        const odb_SequenceNode& nodes);
```

**必需参数**

*name*

一个 odb_String，指定集的名称和存储库键。

*nodes*

[OdbMeshNode](pt02ch61pyo19.md) 对象的序列。例如，对于部件：

```
nodes=part1.nodes[1:5]
```

**可选参数**

无。

**返回值**

一个 OdbSet 对象。

**异常**

InvalidNameError。

### 61.24.2 ElementSet(...)

此方法从 [OdbMeshElement](pt02ch61pyo18.md) 对象数组创建元素集（用于部件实例级集）。

**路径**

```
odb.parts()[*name*].ElementSet
```

```
odb.rootAssembly().instances()[*name*].ElementSet
```

**原型**

```
odb_Set&
ElementSet(const odb_String& name,
           const odb_SequenceElement& elements);
```

**必需参数**

*name*

一个 odb_String，指定集的名称和存储库键。

*elements*

[OdbMeshElement](pt02ch61pyo18.md) 对象的序列。例如，对于部件：

```
elements=instance1.elements[1:5]
```

**可选参数**

无。

**返回值**

一个 OdbSet 对象。

**异常**

InvalidNameError。

### 61.24.3 NodeSet(...)

此方法创建节点集。

**路径**

```
odb.parts()[*name*].NodeSet                   
```

```
odb.rootAssembly().instances()[*name*].NodeSet                   
```

**原型**

```
odb_Set&
NodeSet(const odb_String& name,
        const odb_SequenceInt& nodeLabels);
```

**必需参数**

*name*

一个 odb_String，指定集的名称和存储库键。

*nodeLabels*

一个 odb_SequenceInt，指定节点标签。

**可选参数**

无。

**返回值**

一个 OdbSet 对象。

**异常**

无。

### 61.24.4 NodeSet(...)

此方法创建节点集。

**路径**

```
odb.rootAssembly().NodeSet
```

**原型**

```
odb_Set&
NodeSet(const odb_String& name,
        const odb_SequenceString& instanceNames,
        const odb_SequenceSequenceInt& nodeLabels);
```

**必需参数**

*name*

一个 odb_String，指定集的名称和存储库键。

*instanceNames*

一个 odb_SequenceString，指定 *nodeLabels* 的命名空间。该字符串可以是一个空字符串，表示装配级别的 nodeLabels。

*nodeLabels*

一个 odb_SequenceSequenceInt，指定节点标签。

**可选参数**

无。

**返回值**

一个 OdbSet 对象。

**异常**

无。

### 61.24.5 ElementSet(...)

此方法创建元素集。

**路径**

```
odb.parts()[*name*].ElementSet                   
```

```
odb.rootAssembly().instances()[*name*].ElementSet                   
```

**原型**

```
odb_Set&
ElementSet(const odb_String& name,
           const odb_SequenceInt& elementLabels);
```

**必需参数**

*name*

一个 odb_String，指定集的名称和存储库键。

*elementLabels*

一个 odb_SequenceInt，指定元素标签。

**可选参数**

无。

**返回值**

一个 OdbSet 对象。

**异常**

无。

### 61.24.6 ElementSet(...)

此方法创建元素集。

**路径**

```
odb.rootAssembly().ElementSet
```

**原型**

```
odb_Set&
ElementSet(const odb_String& name,
           const odb_SequenceString& instanceNames,
           const odb_SequenceSequenceInt& elementLabels);
```

**必需参数**

*name*

一个 odb_String，指定集的名称和存储库键。

*instanceNames*

一个 odb_SequenceString，指定 *elementLabels* 的命名空间。该字符串可以是一个空字符串，表示装配级别的 elementLabels。

*elementLabels*

一个 odb_SequenceSequenceInt，指定元素标签。

**可选参数**

无。

**返回值**

一个 OdbSet 对象。

**异常**

无。

### 61.24.7 Surface(...)

此方法创建表面集。

**路径**

```
odb.parts()[*name*].Surface                   
```

```
odb.rootAssembly().instances()[*name*].Surface                   
```

**原型**

```
odb_Set&
Surface(const odb_String& name,
        const odb_SequenceElement& elements,
        const odb_SequenceElementFace& faces);
```

**必需参数**

*name*

一个 odb_String，指定集的名称和存储库键。

*elements*

一个 odb_SequenceElement，指定表面中的元素。

*faces*

一个 odb_SequenceElementFace，指定元素面。

可能的面枚举取决于元素类型，如下表所述：

| 元素类型 | 面枚举 |
| --- | --- |
| 实体元素 | FACE1, FACE2, FACE3, FACE4, FACE5, FACE6 |
| 三维壳元素 | SIDE1, SIDE2 |
| 二维元素 | FACE1, FACE2, FACE3, FACE4 |
| 线单元 | END, END2 |

**可选参数**

无。

**返回值**

一个 OdbSet 对象。

**异常**

无。

### 61.24.8 Surface(...)

此方法创建表面集。

**路径**

```
odb.parts()[*name*].Surface                   
```

```
odb.rootAssembly().instances()[*name*].Surface                   
```

**原型**

```
odb_Set&
Surface(const odb_String& name,
        const odb_SequenceInt& elementLabels,
        const odb_SequenceElementFace& faces);
```

**必需参数**

*name*

一个 odb_String，指定集的名称和存储库键。

*elementLabels*

一个 odb_SequenceInt，指定元素标签。

*faces*

一个 odb_SequenceElementFace，指定元素面。装配集需要 odb_SequenceSequenceElementFace。

**可选参数**

无。

**返回值**

一个 OdbSet 对象。

**异常**

无。

### 61.24.9 Surface(...)

此方法创建表面集。

**路径**

```
odb.rootAssembly().Surface
```

**原型**

```
odb_Set&
Surface(const odb_String& name,
        const odb_SequenceString& instanceNames,
        const odb_SequenceSequenceInt& elementLabels,
        const odb_SequenceSequenceElementFace& faces);
```

**必需参数**

*name*

一个 odb_String，指定集的名称和存储库键。

*instanceNames*

一个 odb_SequenceString，指定 *elementLabels* 的命名空间。此成员仅对装配集有效。该字符串可以是一个空字符串，表示装配级别的 elementLabels。

*elementLabels*

一个 odb_SequenceSequenceInt，指定元素标签。

*faces*

一个 odb_SequenceSequenceElementFace，指定元素面。

**可选参数**

无。

**返回值**

一个 OdbSet 对象。

**异常**

无。

### 61.24.10 成员

OdbSet 对象可以具有以下成员：

**原型**

```
odb_String name() const;
               odb_SequenceString instanceNames();
               odb_Node nodes(int index);
               const odb_SequenceNode& nodes();
               const odb_SequenceNode& nodes(const odb_String& \
                   instanceName); // For an assembly level set
               odb_Element elements(int index);
               const odb_SequenceElement& elements();
               const odb_SequenceElement& elements(const odb_String& \
                   instanceName); // For an assembly level set
               odb_Enum::odb_ElementFaceEnum faces(int index);
               const odb_SequenceElementFace& faces() ;
               const odb_SequenceElementFace& faces(const odb_String& \
                    instanceName); // For an assembly level set
               odb_Enum::odb_SetTypeEnum type() const;
```

*name*

一个 odb_String，指定集的名称和存储库键。

*instanceNames*

一个 odb_SequenceString，指定构成集的节点、元素和面的命名空间。

*nodes*

[OdbMeshNode](pt02ch61pyo19.md) 对象的序列。

*elements*

[OdbMeshElement](pt02ch61pyo18.md) 对象的序列。

*faces*

一个 odb_SequenceElementFace，指定元素面。
