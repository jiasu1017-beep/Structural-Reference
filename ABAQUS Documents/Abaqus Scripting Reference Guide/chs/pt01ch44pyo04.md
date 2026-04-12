# 44.4 MaterialOrientation 对象

MaterialOrientation 对象表示材料属性和复合铺层的取向。

**访问**

```
import section
mdb.models[*name*].parts[*name*].compositeLayups[*i*].orientation
mdb.models[*name*].parts[*name*].materialOrientations[*i*]
import odbAccess
session.odbs[*name*].parts[*name*].materialOrientations[*i*]
session.odbs[*name*].rootAssembly.instances[*name*]\
.materialOrientations[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.materialOrientations[*i*]
```

### 44.4.1 MaterialOrientation(...)

此方法创建 MaterialOrientation 对象。

**Path**

```
mdb.models[*name*].parts[*name*].MaterialOrientation
```

**必需参数**

无。

**可选参数**

*region*

 [Set](pt01ch45pyo04.md) 对象，指定定义材料取向的区域。

*localCsys*

 [DatumCsys](pt01ch15pyo03.md) 对象，指定局部坐标系，或 `None`，描述给定区域的材料取向。在 ODB 中，此成员以前使用 "csys" 访问，但现在已添加对 localCsys 的支持，csys 成员将被弃用。

*axis*

 SymbolicConstant，指定 datum 坐标系的轴，围绕该轴应用额外旋转。对于壳，此轴也是壳法线。可选值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle*

 Float，指定额外旋转的角度（如果从 ODB 而非 MDB 访问，它将是字符串而不是浮点数）。默认值为 0.0。

*stackDirection*

 SymbolicConstant，指定堆叠或厚度方向。可选值为 STACK_1、STACK_2、STACK_3 和 STACK_ORIENTATION。默认值为 STACK_3。

*fieldName*

 String，指定 [DiscreteField](pt01ch21pyo04.md) 对象的名称，指定取向。默认值为空字符串。

*orientationType*

 SymbolicConstant，指定用于定义材料取向的方法。如果 *orientationType*=SYSTEM，则需要 *region* 和 *localCsys* 参数。如果 *orientationType*=FIELD，则需要 *fieldName* 参数。可选值为 GLOBAL、SYSTEM、FIELD、DISCRETE 和 USER。默认值为 GLOBAL。

*normalAxisDirection*

 SymbolicConstant，指定离散取向的法线轴方向定义的轴。可选值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_3。

*normalAxisDefinition*

 SymbolicConstant，指定用于定义离散取向的法线轴方向的方法。可选值为 SURFACE、NORMAL_DATUM 和 NORMAL_VECTOR。默认值为 NORMAL_VECTOR。

*normalAxisRegion*

 [Surface](pt01ch45pyo05.md) 对象，指定其几何法线定义离散取向法线轴的区域。

*normalAxisDatum*

 [DatumAxis](pt01ch15pyo02.md) 对象，指定 Datum Axis，或 `None`，描述离散取向的法线轴方向。

*flipNormalDirection*

 Boolean，指定反转定义的法线轴方向标志。默认值为 OFF。

*normalAxisVector*

 Float 序列，指定定义离散取向法线轴方向的向量。

*primaryAxisDirection*

 SymbolicConstant，指定离散取向的主轴方向定义的轴。可选值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*primaryAxisDefinition*

 SymbolicConstant，指定用于定义离散取向的主轴方向的方法。可选值为 SURFACE、PRIMARY_DATUM 和 PRIMARY_VECTOR。默认值为 PRIMARY_VECTOR。

*primaryAxisRegion*

 [Set](pt01ch45pyo04.md) 对象，指定其几何切线定义离散取向主轴的区域。

*primaryAxisDatum*

 [DatumAxis](pt01ch15pyo02.md) 对象，指定 Datum Axis，或 `None`，描述离散取向的主轴方向。

*flipPrimaryDirection*

 Boolean，指定反转定义的主轴方向标志。默认值为 OFF。

*primaryAxisVector*

 Float 序列，指定定义离散取向主轴方向的向量。

**返回值**

MaterialOrientation 对象。

**异常**

无。

### 44.4.2 ReferenceOrientation(...)

此方法创建 MaterialOrientation 对象。

**Path**

```
mdb.models[*name*].parts[*name*].compositeLayups[*name*].ReferenceOrientation
```

**必需参数**

无。

**可选参数**

*localCsys*

 [DatumCsys](pt01ch15pyo03.md) 对象，指定局部坐标系，或 `None`，描述给定区域的材料取向。在 ODB 中，此成员以前使用 "csys" 访问，但现在已添加对 localCsys 的支持，csys 成员将被弃用。

*axis*

 SymbolicConstant，指定 datum 坐标系的轴，围绕该轴应用额外旋转。对于壳，此轴也是壳法线。可选值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle*

 Float，指定额外旋转的角度（如果从 ODB 而非 MDB 访问，它将是字符串而不是浮点数）。默认值为 0.0。

*stackDirection*

 SymbolicConstant，指定堆叠或厚度方向。可选值为 STACK_1、STACK_2、STACK_3 和 STACK_ORIENTATION。默认值为 STACK_3。

*fieldName*

 String，指定 [DiscreteField](pt01ch21pyo04.md) 对象的名称，指定取向。默认值为空字符串。

*orientationType*

 SymbolicConstant，指定用于定义材料取向的方法。如果 *orientationType*=SYSTEM，则需要 *region* 和 *localCsys* 参数。如果 *orientationType*=FIELD，则需要 *fieldName* 参数。可选值为 GLOBAL、SYSTEM、FIELD、DISCRETE 和 USER。默认值为 GLOBAL。

*additionalRotationField*

 String，指定 [DiscreteField](pt01ch21pyo04.md) 对象的名称，指定额外旋转。默认值为空字符串。

*additionalRotationType*

 SymbolicConstant，指定用于描述当指定了有效取向时的额外旋转的方法。可选值为 ROTATION_NONE、ROTATION_ANGLE 和 ROTATION_FIELD。默认值为 ROTATION_NONE。

*normalAxisDirection*

 SymbolicConstant，指定离散取向的法线轴方向定义的轴。可选值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_3。

*normalAxisDefinition*

 SymbolicConstant，指定用于定义离散取向的法线轴方向的方法。可选值为 SURFACE、NORMAL_DATUM 和 NORMAL_VECTOR。默认值为 NORMAL_VECTOR。

*normalAxisRegion*

 [Surface](pt01ch45pyo05.md) 对象，指定其几何法线定义离散取向法线轴的区域。

*normalAxisDatum*

 [DatumAxis](pt01ch15pyo02.md) 对象，指定 Datum Axis，或 `None`，描述离散取向的法线轴方向。

*flipNormalDirection*

 Boolean，指定反转定义的法线轴方向标志。默认值为 OFF。

*normalAxisVector*

 Float 序列，指定定义离散取向法线轴方向的向量。

*primaryAxisDirection*

 SymbolicConstant，指定离散取向的主轴方向定义的轴。可选值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*primaryAxisDefinition*

 SymbolicConstant，指定用于定义离散取向的主轴方向的方法。可选值为 SURFACE、PRIMARY_DATUM 和 PRIMARY_VECTOR。默认值为 PRIMARY_VECTOR。

*primaryAxisRegion*

 [Set](pt01ch45pyo04.md) 对象，指定其几何切线定义离散取向主轴的区域。

*primaryAxisDatum*

 [DatumAxis](pt01ch15pyo02.md) 对象，指定 Datum Axis，或 `None`，描述离散取向的主轴方向。

*flipPrimaryDirection*

 Boolean，指定反转定义的主轴方向标志。默认值为 OFF。

*primaryAxisVector*

 Float 序列，指定定义离散取向主轴方向的向量。

**返回值**

MaterialOrientation 对象。

**异常**

无。

### 44.4.3 setValues(...)

此方法修改 MaterialOrientation 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [MaterialOrientation](pt01ch44pyo04.md#ker-materialorientation-materialorientation-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 44.4.4 成员

MaterialOrientation 对象的成员与 [MaterialOrientation](pt01ch44pyo04.md#ker-materialorientation-materialorientation-pyc) 方法的参数具有相同的名称和描述。

此外，MaterialOrientation 对象可以具有以下成员：

*additionalRotationType*

 SymbolicConstant，指定用于描述当指定了有效取向时的额外旋转的方法。可选值为 ROTATION_NONE、ROTATION_ANGLE 和 ROTATION_FIELD。默认值为 ROTATION_NONE。

*additionalRotationField*

 String，指定 [DiscreteField](pt01ch21pyo04.md) 对象的名称，指定额外旋转。默认值为空字符串。

