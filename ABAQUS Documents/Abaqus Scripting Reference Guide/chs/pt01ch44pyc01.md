# 44.6 属性分配命令

属性分配命令用于为零件分配和取消分配属性。必须导入 `part` 和 `section` 模块才能访问属性分配命令。

**访问**

```
import part
import section
```

### 44.6.1 assignBeamSectionOrientation(...)

此方法为零件区域分配梁截面取向。

**Path**

```
mdb.models[*name*].parts[*name*].assignBeamSectionOrientation
```

**必需参数**

*region*

 Edge 对象的几何序列的序列，或一维元素的序列。

*method*

 SymbolicConstant，指定分配方法。当前仅支持值 N1_COSINES。

*n1*

三个 Float 的序列，指定梁截面的大致局部 ![](../graphics/ker_eqn00406.gif) 方向。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 44.6.2 assignMaterialOrientation(...)

此方法为区域分配材料取向。

**Path**

```
mdb.models[*name*].parts[*name*].assignMaterialOrientation
```

**必需参数**

*region*

 Vertex、Edge、Face 和 Cell 对象的几何序列的序列，或元素的序列。

*localCsys*

 Datum 对象，指定局部坐标系，或 `None`，表示全局坐标系。

**可选参数**

*axis*

 SymbolicConstant，指定圆柱或球形 datum 坐标系的轴，围绕该轴应用额外旋转。对于壳，此轴也是壳法线。可选值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle*

 Float，指定额外旋转的角度。默认值为 0.0。

**返回值**

无

**异常**

无。

### 44.6.3 assignRebarOrientation(...)

此方法为区域分配钢筋参考取向。

**Path**

```
mdb.models[*name*].parts[*name*].assignRebarOrientation
```

**必需参数**

*region*

 Vertex、Edge、Face 和 Cell 对象的几何序列的序列，或元素的序列。

*localCsys*

 Datum 对象，指定局部坐标系，或 `None`，表示全局坐标系。

**可选参数**

*axis*

 SymbolicConstant，指定圆柱或球形 datum 坐标系的轴，围绕该轴应用额外旋转。对于壳，此轴也是壳法线。可选值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle*

 Float，指定额外旋转的角度。默认值为 0.0。

**返回值**

无

**异常**

无。

### 44.6.4 flipNormal(...)

此方法翻转孤儿网格或二维几何区域的壳或膜单元的法线。

**Path**

```
mdb.models[*name*].parts[*name*].flipNormal
```

**必需参数**

*regions*

 Region 对象，指定要翻转法线的区域。对于 3D 零件，该区域包含 Face 对象或二维三角形或四边形 Element 对象。对于轴对称零件，该区域包含 Edge 对象或线 Elements 对象。

**可选参数**

*referenceRegion*

 二维元素对象，其法线要匹配。如果未指定，则将与给定区域关联的所有法线翻转。*referenceRegion* 参数仅在 regions 参数包含四边形或三角形元素序列时适用。

**返回值**

无

**异常**

无。

### 44.6.5 flipTangent(...)

此方法翻转孤儿网格或一维几何区域的梁或桁架单元的切线。

**Path**

```
mdb.models[*name*].parts[*name*].flipTangent
```

**必需参数**

*regions*

 Region 对象，指定要翻转法线的区域。该区域包含 Edge 对象或一维 Element 对象。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 44.6.6 unassignBeamSectionOrientation(...)

此方法删除梁截面取向分配。

**Path**

```
mdb.models[*name*].parts[*name*].unassignBeamSectionOrientation
```

**必需参数**

*index*

 Int，指定要删除的梁截面取向分配的编号。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 44.6.7 unassignMaterialOrientation(...)

此方法删除材料取向分配。

**Path**

```
mdb.models[*name*].parts[*name*].unassignMaterialOrientation
```

**必需参数**

*index*

 Int，指定要删除的材料分配的编号。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 44.6.8 unassignRebarOrientation(...)

此方法删除钢筋取向分配。

**Path**

```
mdb.models[*name*].parts[*name*].unassignRebarOrientation
```

**必需参数**

*index*

 Int，指定要删除的钢筋参考取向分配的编号。

**可选参数**

无。

**返回值**

无

**异常**

无。

