# 6.5 ModelInstance 对象





ModelInstance 对象是 Model 的实例。

**访问**

```
import assembly
mdb.models[*name*].rootAssembly.modelInstances[*i*]
```

### 6.5.1 Instance(...)

此方法创建 ModelInstance 对象并将其放入 instances 仓库。

**路径**

```
mdb.models[*name*].rootAssembly.Instance
```

**必需参数**

*name*

仓库键。名称必须是有效的 Abaqus 对象名称。

*model*

一个 [Model](pt01ch33pyo01.md) 对象要被实例化。如果模型不存在，则不会创建 ModelInstance 对象。

**可选参数**

*autoOffset*

一个 Boolean，指定是否为新实例应用自动偏移，以将其与现有实例偏移开。默认值为 OFF。

**返回值**

一个 ModelInstance 对象。

**异常**

无。

### 6.5.2 ConvertConstraints()

此方法将实例的定位约束转换为绝对位置。该方法删除实例上的约束特征，但保留空间中的位置。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.5.3 getPosition()

此方法打印应用于 ModelInstance 对象的平移和旋转的总和。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.5.4 translate(...)

此方法将实例平移指定量。

**必需参数**

*vector*

三个 Float 序列，指定平移向量。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.5.5 成员

ModelInstance 对象可以具有以下成员：

*sets*

一个 [Set](pt01ch45pyo04.md) 对象仓库，指定在装配上创建的集合。更多信息，请参见[第 45 章，"区域命令"](pt01ch45.md)。

*surfaces*

一个 [Surface](pt01ch45pyo05.md) 对象仓库，指定在装配上创建的表面。更多信息，请参见[第 45 章，"区域命令"](pt01ch45.md)。

*vertices*

一个 [VertexArray](pt01ch07pyo15.md) 对象。

*edges*

一个 [EdgeArray](pt01ch07pyo03.md) 对象。

*elements*

一个 [MeshElementArray](pt01ch31pyo05.md) 对象。

*nodes*

一个 [MeshNodeArray](pt01ch31pyo09.md) 对象。

*datums*

一个 [Datum](pt01ch15pyo01.md) 对象仓库。

*referencePoints*

一个 [ReferencePoint](pt01ch07pyo13.md) 对象仓库。




