# 7.5 Face 对象





Faces 是二维几何区域。

**访问**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].allInternalSurfaces[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].allSets[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].allSurfaces[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].sets[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].surfaces[*name*].faces[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.faces[*i*]
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.allinstances.surfaces[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.allInternalSets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.allInternalSurfaces[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.allSets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.allSurfaces[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].surfaces[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].surfaces[*name*]\
.faces[*i*]
mdb.models[*name*].rootAssembly.sets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.surfaces[*name*].faces[*i*]
```

### 7.5.1 getCentroid()

此方法返回面的质心。

**参数**

无。

**返回值**

一个 Float 序列，指定面质心的 *X*-、*Y*- 和 *Z*- 坐标。

**异常**

无。

### 7.5.2 getCurvature(...)

此方法返回面上某个位置处的曲率信息。

**必需参数**

*point*

一个元组，指定要获得曲率的点的 *X*-、*Y*- 和 *Z* 坐标。如果 *point* 不在面上，它将被投影到面上。此参数与 *uParam* 和 *vParam* 互斥。

*uParam*

一个 Float，指定要计算曲率的归一化 *U* 参数值。此值必须介于 (0,1) 之间。*vParam* 也必须指定。此参数与 *point* 互斥。

*vParam*

一个 Float，指定要计算曲率的归一化 *V* 参数值。此值必须介于 (0,1) 之间。

**可选参数**

无。

**返回值**

一个字典，键为 'evaluationPoint'、'principalAxis1'、'principalAxis2'、'curvature1'、'curvature2' 和 'gaussianCurvature'。其中 evaluationPoint 指定计算曲率的位置。'principalAxis1' 和 'principalAxis2' 指指定两个主轴的向量。'curvature1' 和 'curvature2' 指定沿两个主轴的曲率。

**异常**

无。

### 7.5.3 getElements()

此方法返回与面关联的元素对象数组。

**参数**

无。

**返回值**

一个 [MeshElementArray](pt01ch31pyo05.md) 对象，即 [MeshElement](pt01ch31pyo05.md) 对象的序列。

**异常**

无。

### 7.5.4 getElementFaces(...)

此方法返回网格面对象数组。每个网格面对象包含元素标签和位于几何面一侧的元素面。

**必需参数**

无。

**可选参数**

*faceSide*

一个 symbolic constant，指定要从中检索元素面的几何实体的哪一侧。可能的值为 *SIDE1*、*SIDE2* 和 *BOTH_SIDES*。默认值为 *BOTH_SIDES*。对于壳面，此选项被忽略。

**返回值**

一个 [MeshFaceArray](pt01ch31pyo08.md) 对象，即 [MeshFace](pt01ch31pyo08.md) 对象的序列。

**异常**

无。

### 7.5.5 getNodes(...)

此方法返回网格节点对象数组。每个网格节点对象包含位于几何面上的节点的标签。

**必需参数**

无。

**可选参数**

*faceSide*

一个 symbolic constant，指定要从中检索节点的几何实体的哪一侧。可能的值为 *SIDE1*、*SIDE2* 和 *BOTH_SIDES*。默认值为 *BOTH_SIDES*。对于壳面和对于两侧具有兼容网格的面，此选项被忽略。否则，输出面的指定侧上的节点。

**返回值**

一个 [MeshNodeArray](pt01ch31pyo09.md) 对象，即 [MeshNode](pt01ch31pyo09.md) 对象的序列。

**异常**

无。

### 7.5.6 getNormal(...)

此方法返回面上指定位置处的法线。可以使用可选的 *point* 参数获取面上不同位置的法线。

**必需参数**

无。

**可选参数**

*point*

一个元组，指定要获得面的法线的点的 *X*-、*Y*- 和 *Z* 坐标。如果 *point* 不在面上，它将被投影到面上。

**返回值**

一个 Float 序列，指定面的法线的 *X*-、*Y*- 和 *Z*- 分量。

**异常**

如果提供了可选参数 *point* 但点无法投影到面上，则引发异常。

无。

### 7.5.7 getSize(...)

此方法返回一个 Float，表示面的面积。

**必需参数**

无。

**可选参数**

* printResults*

一个 Bool，指定是否打印详细输出。默认值为 True。

**返回值**

一个 Float。

**异常**

无。

### 7.5.8 getEdges()

此方法返回一个由面上边缘 ID 组成的序列。

**参数**

无。

**返回值**

一个整数元组。

**异常**

无。

### 7.5.9 getVertices()

此方法返回一个由面顶点 ID 组成的序列。

**参数**

无。

**返回值**

一个整数元组。

**异常**

无。

### 7.5.10 getCells()

此方法返回一个由面所属单元格的单元格 ID 组成的序列。

**参数**

无。

**返回值**

一个整数元组。

**异常**

无。

### 7.5.11 getAdjacentFaces()

此方法返回一个数组，包含共享面至少一个边缘的面对象。

**参数**

无。

**返回值**

一个 [FaceArray](pt01ch07pyo05.md) 对象，即 Face 对象的序列。

**异常**

无。

### 7.5.12 getFacesByFaceAngle(...)

此方法返回一个面对象数组，通过递归查找位于小于或等于指定角度的相邻面获得。

**必需参数**

*angle*

一个 float，指定面角值。

**可选参数**

无。

**返回值**

一个 [FaceArray](pt01ch07pyo05.md) 对象，即 Face 对象的序列。

**异常**

无。

### 7.5.13 getFacesByCurvature()

此方法返回一个面对象数组，通过递归查找共享相同曲率的相邻面获得。

**参数**

无。

**返回值**

一个 [FaceArray](pt01ch07pyo05.md) 对象，即 Face 对象的序列。

**异常**

无。

### 7.5.14 isNormalFlipped()

此方法确定面的法线是否通过 Part 对象上的 `FlipNormal` 方法从其默认方向翻转。

**参数**

无。

**返回值**

如果法线被翻转则为 True，否则为 False。

**异常**

无。

### 7.5.15 成员

Face 对象具有以下成员：

*index*

一个 Int，指定面在 FaceArray 中的索引。

*isReferenceRep*

一个 Boolean，指定面是否属于零件或实例的参考表示。

*pointOn*

一个 Float 元组元组，指定坐标。对于壳的面，*pointOn* 指定位于面上的一点的 *X*-、*Y*- 和 *Z*- 坐标以及指向面的法线的 *X*-、*Y*- 和 *Z*- 分量。

对于实体的面，*pointOn* 指定位于面上的一点的 *X*-、*Y*- 和 *Z*- 坐标。

*featureName*

一个 Float 元组，指定创建此面的特征名称。

*instanceName*

一个 Float 元组，指定此面的零件实例名称（如果适用）。




