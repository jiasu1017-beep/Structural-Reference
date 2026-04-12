# 7.2 CellArray 对象





CellArray 是 [Cell](pt01ch07pyo01.md) 对象的序列。

**访问**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].cells
mdb.models[*name*].parts[*name*].allSets[*name*].cells
mdb.models[*name*].parts[*name*].cells
mdb.models[*name*].parts[*name*].sets[*name*].cells
import assembly
mdb.models[*name*].rootAssembly.allinstances.cells
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].cells
mdb.models[*name*].rootAssembly.allInternalSets[*name*].cells
mdb.models[*name*].rootAssembly.allSets[*name*].cells
mdb.models[*name*].rootAssembly.instances[*name*].cells
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].cells
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].cells
mdb.models[*name*].rootAssembly.sets[*name*].cells
```

### 7.2.1 findAt(...)

此方法返回位于给定坐标处的 CellArray 中的对象。`findAt` 最初使用 ACIS 容差 1E-6。因此，`findAt` 返回任意点指定处或距离任意点小于 1E-6 的任何实体。如果未找到任何内容，`findAt` 使用不精确几何的容差（仅适用于不精确几何实体）。任意点不能被第二个单元格共享。如果两个单元格在任意点相交或重合，`findAt` 会选择它遇到的第一个单元格，您不应依赖返回值的一致性。

`findAt` 将始终尝试在零件或装配实例中的所有单元格中查找对象，而不会将自己限制为子集，即使 CellArray 表示这样的子集。

**必需参数**

*coordinates*

一个 Float 序列，指定要查找的对象的 *X*-、*Y*- 和 *Z*- 坐标。

`findAt` 根据输入类型返回 Cell 对象或 Cell 对象序列。如果 *coordinates* 是 Float 序列，则 `findAt` 返回该点的 Cell 对象。如果 *coordinates* 是 Float 序列的序列，则 `findAt` 返回给定位置处的 Cell 对象序列。Float 序列的序列必须是点数据和法线数据的序列，而不是点数据的序列。例如：

```
cells1 = myCrackedBlockInstance.cells.findAt(
                            ((5.5, -8.3, 294.2),),
                            ((12.1, -8.3, 287.8),),
                            ((14.4, -10.4, 285.5),),)
```

**可选参数**

*printWarning*

一个 Boolean，指定如果在该位置未找到实体，是否向 CLI 打印消息。默认值为 True。

**返回值**

一个 Cell 对象。

**异常**

无。

### 7.2.2 getSequenceFromMask(...)

此方法返回使用指定 *mask* 标识的 CellArray 中的对象。当 [JournalOptions](pt01ch47pyo06.md) 设置为 COMPRESSEDINDEX 时，会生成此命令。当涉及大量对象时，此方法非常高效。

**必需参数**

*mask*

一个 String，指定对象或对象。

**可选参数**

无。

**返回值**

一个 Cell 对象或 Cell 对象序列。

**异常**

如果结果序列为空，则抛出异常。

```
Error: The mask results in an empty sequence
```

### 7.2.3 getMask()

此方法返回一个字符串，指定对象或对象。

**参数**

无。

**返回值**

一个 String，指定对象或对象。

**异常**

无。

### 7.2.4 getByBoundingBox(...)

此方法返回位于指定边界框内的单元格对象数组。

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

一个 CellArray 对象，即 [Cell](pt01ch07pyo01.md) 对象的序列。

**异常**

无。

### 7.2.5 getByBoundingCylinder(...)

此方法返回位于指定边界圆柱体内的单元格对象数组。

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

一个 CellArray 对象，即 [Cell](pt01ch07pyo01.md) 对象的序列。

**异常**

无。

### 7.2.6 getByBoundingSphere(...)

此方法返回位于指定边界球体内的单元格对象数组。

**必需参数**

*center*

一个元组，表示球体中心的 *X*-、*Y*- 和 *Z*- 坐标。

*radius*

一个 float，指定球体的半径。

**可选参数**

无。

**返回值**

一个 CellArray 对象，即 [Cell](pt01ch07pyo01.md) 对象的序列。

**异常**

无。

### 7.2.7 getBoundingBox()

此方法返回一个字典，包含两个元组，表示包含单元格序列的最小尺寸边界框的最小和最大边界值。

**参数**

无。

**返回值**

一个 Dictionary 对象，包含以下项目：

*low*：三个 float 元组，表示边界框的最小 *X*-、*Y*- 和 *Z*- 边界值。

*high*：三个 float 元组，表示边界框的最大 *X*-、*Y*- 和 *Z*- 边界值。

**异常**

无。

### 7.2.8 成员

CellArray 对象没有成员。




