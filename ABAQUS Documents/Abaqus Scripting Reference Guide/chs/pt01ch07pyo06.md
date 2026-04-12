# 7.6 FaceArray 对象





FaceArray 是 [Face](pt01ch07pyo05.md) 对象的序列。如果零件被修改，则必须为该零件更新 FaceArray。

**访问**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].faces
mdb.models[*name*].parts[*name*].allInternalSurfaces[*name*].faces
mdb.models[*name*].parts[*name*].allSets[*name*].faces
mdb.models[*name*].parts[*name*].allSurfaces[*name*].faces
mdb.models[*name*].parts[*name*].faces
mdb.models[*name*].parts[*name*].sets[*name*].faces
mdb.models[*name*].parts[*name*].surfaces[*name*].faces
import assembly
mdb.models[*name*].rootAssembly.allinstances.faces
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].faces
mdb.models[*name*].rootAssembly.allinstances.surfaces[*name*].faces
mdb.models[*name*].rootAssembly.allInternalSets[*name*].faces
mdb.models[*name*].rootAssembly.allInternalSurfaces[*name*].faces
mdb.models[*name*].rootAssembly.allSets[*name*].faces
mdb.models[*name*].rootAssembly.allSurfaces[*name*].faces
mdb.models[*name*].rootAssembly.instances[*name*].faces
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].faces
mdb.models[*name*].rootAssembly.instances[*name*].surfaces[*name*].faces
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].faces
mdb.models[*name*].rootAssembly.modelInstances[*i*].surfaces[*name*].faces
mdb.models[*name*].rootAssembly.sets[*name*].faces
mdb.models[*name*].rootAssembly.surfaces[*name*].faces
```

### 7.6.1 findAt(...)

此方法返回位于给定坐标处的 FaceArray 中的对象。

`findAt` 最初使用 ACIS 容差 1E-6。因此，`findAt` 返回任意点指定处或距离任意点小于 1E-6 的任何面。如果未找到任何内容，`findAt` 使用不精确几何的容差（仅适用于不精确几何实体）。任意点不能被第二个面共享。如果两个面相交或重合，`findAt` 会选择它遇到的第一个面，您不应依赖返回值的一致性。

`findAt` 将始终尝试在零件或装配实例中的所有面中查找对象，而不会将自己限制为子集，即使 FaceArray 表示这样的子集。

**必需参数**

*coordinates*

一个 Float 序列，指定要查找的对象的 *X*-、*Y*- 和 *Z*- 坐标。

`findAt` 根据输入类型返回 Face 对象或 Face 对象序列。
- 如果 *coordinates* 是 Float 序列，则 `findAt` 返回该点的 Face 对象。
- 如果省略 *coordinates* 关键字参数，则 `findAt` 接受描述每个面的坐标和法线的序列序列作为参数，并返回给定位置处的 Face 对象序列。如果省略 *coordinates* 关键字参数，则还必须省略 *normal* 参数。``` faces = f.findAt(((-16.438578, -41.835673, -24.19804), ), ((25.210364, -35.689868, 1.860314), ), ((26.727683, -38.207055, 4.164759), )) ```

**可选参数**

*normal*

一个 Float 序列，指定指示面法线的向量的 *X*-、*Y*- 和 *Z*- 分量。

*printWarning*

一个 Boolean，指定如果在该位置未找到实体，是否向 CLI 打印消息。默认值为 True。

**返回值**

一个 Face 对象。

**异常**

无。

### 7.6.2 getSequenceFromMask(...)

此方法返回使用指定 *mask* 标识的 FaceArray 中的对象。当 [JournalOptions](pt01ch47pyo06.md) 设置为 COMPRESSEDINDEX 时，会生成此命令。当涉及大量对象时，此方法非常高效。

**必需参数**

*mask*

一个 String，指定对象或对象。

**可选参数**

无。

**返回值**

一个 Face 对象或 Face 对象序列。

**异常**

无。

### 7.6.3 getMask()

此方法返回一个字符串，指定对象或对象。

**参数**

无。

**返回值**

一个 String，指定对象或对象。

**异常**

无。

### 7.6.4 getByBoundingBox(...)

此方法返回位于指定边界框内的面对象数组。

**必需参数**

无。

**可选参数**

*xMin*

一个 float，指定边界框的最小 *X* 边界。

*yMin*

一个 float，指定边界框的最小 *Y* 边界。

*zMin*

一个 float，指定边界框的最小 *Z* 边界。

*xMax*

一个 float，指定边界框的最大 *X* 边界。

*yMax*

一个 float，指定边界框的最大 *Y* 边界。

*zMax*

一个 float，指定边界框的最大 *Z* 边界。

**返回值**

一个 FaceArray 对象，即 [Face](pt01ch07pyo05.md) 对象的序列。

**异常**

无。

### 7.6.5 getByBoundingCylinder(...)

此方法返回位于指定边界圆柱体内的面对象数组。

**必需参数**

*center1*

圆柱体第一端中心的 *X*-、*Y*- 和 *Z*- 坐标元组。

*center2*

圆柱体第二端中心的 *X*-、*Y*- 和 *Z*- 坐标元组。

*radius*

一个 float，指定圆柱体的半径。

**可选参数**

无。

**返回值**

一个 FaceArray 对象，即 [Face](pt01ch07pyo05.md) 对象的序列。

**异常**

无。

### 7.6.6 getByBoundingSphere(...)

此方法返回位于指定边界球体内的面对象数组。

**必需参数**

*center*

一个元组，表示球体中心的 *X*-、*Y*- 和 *Z*- 坐标。

*radius*

一个 float，指定球体的半径。

**可选参数**

无。

**返回值**

一个 FaceArray 对象，即 [Face](pt01ch07pyo05.md) 对象的序列。

**异常**

无。

### 7.6.7 getBoundingBox()

此方法返回一个字典，包含两个元组，表示包含面序列的最小尺寸边界框的最小和最大边界值。

**参数**

无。

**返回值**

一个 Dictionary 对象，包含以下项目：

*low*：三个 float 元组，表示边界框的最小 *X*-、*Y*- 和 *Z*- 边界值。

*high*：三个 float 元组，表示边界框的最大 *X*-、*Y*- 和 *Z*- 边界值。

**异常**

无。

### 7.6.8 getClosest(...)

此方法返回 FaceArray 中离给定点集最近的对象或对象，给定点不必位于 FaceArray 中的面上。

**必需参数**

*coordinates*

一个 float 序列的序列，其中每个 float 序列描述一个点的 *X*-、*Y*- 和 *Z*- 坐标。

```
r=f.getClosest(coordinates=((20.0,20.0,10.0),(-1.0, -15.0, 15),))
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
(mdb.models['Model-1'].parts['Part-1'].faces[0],
                                 (15.7090625762939, 20.0, 10.0))
```

**可选参数**

*searchTolerance*

一个 double，指定最近对象必须位于的距离内。默认值为父零件/实例大小的一半。

**返回值**

此方法返回一个字典对象。字典的键是 *coordinates* 中指定输入点在元组中的位置，从索引 0 开始。如果找到最近的面，则值是一个包含两个对象的序列。序列中的第一个对象是一个 [Face](pt01ch07pyo05.md)，靠近键所指的输入点。序列中的第二个对象是一个 float 序列，指定 [Face](pt01ch07pyo05.md) 上到给定点的最近点的 *X*-、*Y*- 和 *Z*- 位置。请参阅上面的程序列表。

**异常**

如果结果序列为空，则抛出异常。

```
Error: The mask results in an empty sequence
```

### 7.6.9 成员

FaceArray 对象没有成员。




