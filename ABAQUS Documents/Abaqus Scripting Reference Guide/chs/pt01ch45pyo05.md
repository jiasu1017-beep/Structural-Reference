# 45.5 Surface 对象

Surface 对象存储从装配中选择的曲面。曲面由几何或离散实体组成，但不能同时包含两者。Surface 对象实例可从 Assembly 对象的 *surface* 成员获取。

**访问**

```
import part
mdb.models[*name*].parts[*name*].allInternalSurfaces[*name*]
mdb.models[*name*].parts[*name*].allSurfaces[*name*]
mdb.models[*name*].parts[*name*].surfaces[*name*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.surfaces[*name*]
mdb.models[*name*].rootAssembly.allInternalSurfaces[*name*]
mdb.models[*name*].rootAssembly.allSurfaces[*name*]
mdb.models[*name*].rootAssembly.instances[*name*].surfaces[*name*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].surfaces[*name*]
mdb.models[*name*].rootAssembly.surfaces[*name*]
```

### 45.5.1 Surface(...)

 此方法从模型数据库中的对象序列创建曲面。曲面将应用于参数指定的面。例如：

```
surface=mdb.models['Model-1'].parts['Part-1'].Surface(side1Faces=side1Faces, name='Surf-1')
```

**Path**

```
mdb.models[*name*].parts[*name*].Surface
```

```
mdb.models[*name*].rootAssembly.Surface
```

**必需参数**

 在三维实体面上，您可以使用以下参数：
- *side1Faces*
- *side2Faces*

 在三维壳面上，您可以使用以下参数：
- *side1Faces*
- *side2Faces*
- *side12Faces*

 在三维线边缘上，您可以使用以下参数：
- *end1Edges*
- *end2Edges*
- *circumEdges*

 在三维、二维或轴对称边缘上，您可以使用以下参数：
- *side1Edges*
- *side2Edges*

 在二维或轴对称壳单元上，您可以使用以下参数：
- *face1Elements*
- *face2Elements*
- *face3Elements*
- *face14Elements*

 在实体单元上，您可以使用以下参数：
- *face1Elements*
- *face2Elements*
- *face3Elements*
- *face4Elements*
- *face5Elements*
- *face6Elements*

 在三维壳单元上，您可以使用以下参数：
- *side1Elements*
- *side2Elements*
- *side12Elements*

 在三维线单元上，您可以使用以下参数：
- *end1Elements*
- *end2Elements*
- *circumElements*

 在二维或轴对称线单元上，您可以使用以下参数：
- *side1Elements*
- *side2Elements*

*name*

 String，指定存储库键。默认值为空字符串。

**可选参数**

*side1Elements*

 [MeshElement](pt01ch31pyo05.md) 对象序列（曲面适用于元素的 SIDE1）。默认值为 `None`。

*side2Elements*

 [MeshElement](pt01ch31pyo05.md) 对象序列（曲面适用于元素的 SIDE2）。默认值为 `None`。

*side12Elements*

 MeshElement 对象序列（曲面同时适用于元素的 SIDE1 和 SIDE2）。默认值为 `None`。

*end1Elements*

 MeshElement 对象序列（曲面适用于元素的 END1）。默认值为 `None`。

*end2Elements*

 MeshElement 对象序列（曲面适用于元素的 END2）。默认值为 `None`。

*circumElements*

 MeshElement 对象序列（曲面适用于元素的周向）。默认值为 `None`。

*face1Elements*

 MeshElement 对象序列（曲面适用于元素的 FACE1）。默认值为 `None`。

*face2Elements*

 MeshElement 对象序列（曲面适用于元素的 FACE2）。默认值为 `None`。

*face3Elements*

 MeshElement 对象序列（曲面适用于元素的 FACE3）。默认值为 `None`。

*face4Elements*

 MeshElement 对象序列（曲面适用于元素的 FACE4）。默认值为 `None`。

*face5Elements*

 MeshElement 对象序列（曲面适用于元素的 FACE5）。默认值为 `None`。

*face6Elements*

 MeshElement 对象序列（曲面适用于元素的 FACE6）。默认值为 `None`。

*side1Faces*

 Face 对象序列（曲面适用于面的 SIDE1）。默认值为 `None`。

*side2Faces*

 Face 对象序列（曲面适用于面的 SIDE2）。默认值为 `None`。

*side12Faces*

 Face 对象序列（曲面同时适用于面的 SIDE1 和 SIDE2）。默认值为 `None`。

*side1Edges*

 Edge 对象序列（曲面适用于边缘的 SIDE1）。默认值为 `None`。

*side2Edges*

 Edge 对象序列（曲面适用于边缘的 SIDE2）。默认值为 `None`。

*end1Edges*

 Edge 对象序列（曲面适用于边缘的 END1）。默认值为 `None`。

*end2Edges*

 Edge 对象序列（曲面适用于边缘的 END2）。默认值为 `None`。

*circumEdges*

 Edge 对象序列（曲面适用于边缘的周向）。默认值为 `None`。

**返回值**

Surface 对象。

**异常**

InvalidNameError。

### 45.5.2 SurfaceByBoolean(...)

此方法通过对两个或多个输入曲面执行布尔运算来创建曲面。

**Path**

```
mdb.models[*name*].parts[*name*].SurfaceByBoolean
```

```
mdb.models[*name*].rootAssembly.SurfaceByBoolean
```

**必需参数**

*name*

 String，指定存储库键。

*surfaces*

 Surface 对象序列。

**可选参数**

*operation*

 SymbolicConstant，指定要执行的布尔运算。可选值为 UNION、INTERSECTION 和 DIFFERENCE。默认值为 UNION。请注意，如果指定了 DIFFERENCE，则给定输入曲面的顺序很重要；指定在第一个之后的所有曲面将从第一个中减去。

**返回值**

Surface 对象。

**异常**

InvalidNameError。

### 45.5.3 SurfaceFromElsets(...)

此方法从模型数据库中的元素集序列创建曲面。

**Path**

```
mdb.models[*name*].rootAssembly.SurfaceFromElsets
```

**必需参数**

*name*

 String，指定存储库键。

*elementSetSeq*

元素集序列。例如：

```
elementSetSeq=((elset1, S1),(elset2, S2))
```
其中 `elset1=mdb.models[*name*].rootAssembly.sets['Clutch']`，S1 和 S2 表示元素集的面。

**可选参数**

无。

**返回值**

Surface 对象。

**异常**

InvalidNameError。

### 45.5.4 成员

Surface 对象可以具有以下成员：

*edges*

 [EdgeArray](pt01ch07pyo03.md) 对象。

*faces*

 [FaceArray](pt01ch07pyo05.md) 对象。

*elements*

 [MeshElementArray](pt01ch31pyo05.md) 对象。

*nodes*

 [MeshNodeArray](pt01ch31pyo09.md) 对象。

*sides*

 SymbolicConstant 元组，指定面；例如，(SIDE1, SIDE2)。

*instances*

 Int 元组，指定实例。此成员不适用于输出数据库上的 Surface 对象。

