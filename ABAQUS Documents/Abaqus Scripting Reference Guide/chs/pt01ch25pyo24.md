# 25.24 ContactStd 对象

ContactStd 对象在 Abaqus/Standard 分析期间定义接触域及相关的接触属性。

ContactStd 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.24.1 ContactStd(...)

此方法创建一个 ContactStd 对象。

**路径**

```
mdb.models[*name*].ContactStd
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建此接触交互的步骤名称。

**可选参数**

*useAllstar*

布尔值，指定接触表面对是否由模型中所有外部面组成。

*globalSmoothing*

布尔值，指定是否自动对所有符合条件的表面应用表面平滑（几何校正）。默认值为 ON。

*includedPairs*

[RegionPairs](pt01ch25pyo59.md) 对象，指定包含在接触中的域对。

*excludedPairs*

[RegionPairs](pt01ch25pyo59.md) 对象，指定排除在接触之外的域对。

*contactPropertyAssignments*

[ContactPropertyAssignment](pt01ch25pyo22.md) 对象，指定接触域中的接触属性分配。

*surfaceThicknessAssignments*

[SurfaceThicknessAssignment](pt01ch25pyo73.md) 对象，指定接触域中的表面厚度分配。

*surfaceOffsetAssignments*

[SurfaceOffsetAssignment](pt01ch25pyo72.md) 对象，指定接触域中的表面偏移分数分配。

*surfaceFeatureAssignments*

[SurfaceFeatureAssignment](pt01ch25pyo71.md) 对象，指定接触域中的表面特征角度分配。

*masterSlaveAssignments*

[MasterSlaveAssignment](pt01ch25pyo50.md) 对象，指定接触域中的主-从分配。

*initializationAssignments*

[InitializationAssignment](pt01ch25pyo47.md) 对象，指定接触域中的接触初始化分配。

*stabilizationAssignments*

[StabilizationAssignment](pt01ch25pyo65.md) 对象，指定接触域中的接触稳定化分配。

*smoothingAssignments*

[SmoothingAssignment](pt01ch25pyo64.md) 对象，指定接触域中的表面平滑分配。

**返回值**

ContactStd 对象。

**异常**

无。

### 25.24.2 ContactStd(...)

此方法创建一个 ContactStd 对象。

**路径**

```
mdb.models[*name*].ContactStd
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建此接触交互的步骤名称。

**可选参数**

*globalSmoothing*

布尔值，指定是否自动对所有符合条件的表面应用表面平滑（几何校正）。默认值为 ON。

*useAllstar*

布尔值，指定接触表面对是否由模型中所有外部面组成。

*includedPairs*

[Region](pt01ch45pyo03.md) 对象或 SymbolicConstants 对的序列，指定接触中的表面对。 SymbolicConstants 的可能值为 ALLSTAR 和 SELF。此参数仅在 *useAllstar*=OFF 时有效。

*excludedPairs*

[Region](pt01ch45pyo03.md) 对象或 SymbolicConstants 对的序列，指定排除在接触中的表面对。 SymbolicConstants 的可能值为 ALLSTAR 和 SELF。

*contactPropertyAssignments*

元组序列，指定每个表面对的属性分配。每个元组包含三个条目：
- [Region](pt01ch45pyo03.md) 对象或 SymbolicConstant GLOBAL。
- [Region](pt01ch45pyo03.md) 对象或 SymbolicConstant SELF。
- 字符串，指定与此域对关联的 [InteractionProperty](pt01ch25pyo48.md) 对象。

*surfaceFeatureAssignments*

元组序列，指定接触域中的表面特征角度分配。每个元组包含两个条目：
- 指定表面特征角度被分配的区域的区域对象或 SymbolicConstant GLOBAL。
- 浮点数或 SymbolicConstant，指定在接触定义中使用的覆盖特征角度值。 SymbolicConstants 的可能值为 PERIMETER 或 NONE。

*surfaceThicknessAssignments*

元组序列，指定接触域中的表面厚度分配。每个元组包含三个条目：
- 指定表面厚度被分配的区域的区域对象或 SymbolicConstant GLOBAL。
- 浮点数或 SymbolicConstant，指定在接触定义中使用的覆盖厚度值。可以指定 SymbolicConstant ORIGINAL 代替浮点值。
- 浮点数，指定乘以第二条目中指定厚度值的比例因子。

*surfaceOffsetAssignments*

元组序列，指定接触域中的表面偏移分数分配。每个元组包含两个条目：
- 指定表面偏移分数被分配的区域的区域对象或 SymbolicConstant GLOBAL。
- 浮点数或 SymbolicConstant，指定在接触定义中使用的偏移分数值。 SymbolicConstants 的可能值为 ORIGINAL、SPOS 或 SNEG。

*masterSlaveAssignments*

元组序列，指定接触域中的主-从分配。每个元组包含三个条目：
- 指定定义主-从分配的第一个表面的区域对象或 SymbolicConstant GLOBAL。
- 指定主-从分配定义中第二个表面的区域对象。
- SymbolicConstant，指定第一个表面的状态。可能的值为 MASTER、SLAVE 和 BALANCED。

*initializationAssignments*

元组序列，指定每个表面对的接触初始化数据。每个元组包含三个条目：
- [Region](pt01ch45pyo03.md) 对象或 SymbolicConstant GLOBAL。
- [Region](pt01ch45pyo03.md) 对象或 SymbolicConstant SELF。
- 字符串，指定与此域对关联的 [StdInitialization](pt01ch25pyo67.md) 对象。

*stabilizationAssignments*

元组序列，指定每个表面对的接触稳定化。每个元组包含三个条目：
- [Region](pt01ch45pyo03.md) 对象或 SymbolicConstant GLOBAL。
- [Region](pt01ch45pyo03.md) 对象或 SymbolicConstant SELF。
- 字符串，指定与此域对关联的 [StdStabilization](pt01ch25pyo68.md) 对象。

*smoothingAssignments*

元组序列，指定接触域中的表面平滑分配。每个元组包含两个条目：
- 指定平滑选项被分配的表面的区域对象。
- SymbolicConstant，指定在接触定义中使用的平滑选项。 SymbolicConstants 的可能值为 NONE、REVOLUTION、SPHERICAL 或 TOROIDAL。

**返回值**

ContactStd 对象。

**异常**

无。

### 25.24.3 成员

ContactStd 对象可以具有以下成员：

*name*

字符串，指定存储库键。

*globalSmoothing*

布尔值，指定是否自动对所有符合条件的表面应用表面平滑（几何校正）。默认值为 ON。

*includedPairs*

[RegionPairs](pt01ch25pyo59.md) 对象，指定包含在接触中的域对。

*excludedPairs*

[RegionPairs](pt01ch25pyo59.md) 对象，指定排除在接触之外的域对。

*contactPropertyAssignments*

[ContactPropertyAssignment](pt01ch25pyo22.md) 对象，指定接触域中的接触属性分配。

*surfaceThicknessAssignments*

[SurfaceThicknessAssignment](pt01ch25pyo73.md) 对象，指定接触域中的表面厚度分配。

*surfaceOffsetAssignments*

[SurfaceOffsetAssignment](pt01ch25pyo72.md) 对象，指定接触域中的表面偏移分数分配。

*masterSlaveAssignments*

[MasterSlaveAssignment](pt01ch25pyo50.md) 对象，指定接触域中的主-从分配。

*initializationAssignments*

[InitializationAssignment](pt01ch25pyo47.md) 对象，指定接触域中的接触初始化分配。

*stabilizationAssignments*

[StabilizationAssignment](pt01ch25pyo65.md) 对象，指定接触域中的接触稳定化分配。

*smoothingAssignments*

[SmoothingAssignment](pt01ch25pyo64.md) 对象，指定接触域中的表面平滑分配。

*surfaceFeatureAssignments*

[SurfaceFeatureAssignment](pt01ch25pyo71.md) 对象，指定接触域中的表面特征角度分配。

### 25.24.4 对应的分析关键字

| [*CONTACT](../key/key-link.md#usb-kws-hcontact) |
| --- |



