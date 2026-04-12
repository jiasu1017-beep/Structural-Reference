# 21.4 DiscreteField 对象





DiscreteField 对象定义一个变化场，其值对应于域内离散的点。

DiscreteField 对象派生自 [Field](pt01ch21pyo01.md) 对象。

**访问**

```
import fields
mdb.models[*name*].discreteFields[*name*]
```

### 21.4.1 DiscreteField(...)

此方法创建 DiscreteField 对象。

**路径**

```
mdb.models[*name*].DiscreteField
```

**必需参数**

*name*

一个 String，指定存储库键。

*defaultValues*

一个 Float 序列，指定默认值序列。

*fieldType*

一个 SymbolicConstant 或一个 Int，指定此离散场表示的数据类型。可能的值为 SCALAR、ORIENTATION 和 PRESCRIBEDCONDITION_DOF。

**可选参数**

*location*

一个 SymbolicConstant 或一个 Int，指定域数据的位置。可能的值为 NODES 和 ELEMENTS。默认值为 NODES。

*dataWidth*

一个 Int，指定所提供数据的宽度。默认值为 1。

*data*

一个 [DataTableArray](pt01ch21pyo03.md) 对象。

*description*

一个 String，指定场的描述。默认值为空字符串。

*orientationType*

一个 SymbolicConstant，指定用于方向的离散场所描述的坐标系类型。可能的值为 CARTESIAN、CYLINDRICAL 和 SPHERICAL。默认值为 CARTESIAN。

*partLevelOrientation*

一个 Boolean，指定方向是否以部件级坐标描述。默认值为 OFF。

**返回值**

一个 DiscreteField 对象。

**异常**

AbaqusException。

### 21.4.2 DiscreteFieldByVolumeFraction(...)

此方法创建 DiscreteField 对象，表示每个欧拉实例中被参考实例占据的体积分数。

**路径**

```
mdb.models[*name*].rootAssembly.DiscreteFieldByVolumeFraction
```

**必需参数**

*name*

一个 String，指定存储库键。

*eulerianInstance*

一个 [PartInstance](pt01ch06pyo04.md) 对象，指定要计算体积分数值的单元。

*referenceInstance*

一个 [PartInstance](pt01ch06pyo04.md) 对象，指定包含材料或为空的区域。

**可选参数**

*accuracy*

一个 SymbolicConstant，指定计算体积分数时使用的精度水平。可能的值为 LOW、MEDIUM 或 HIGH。默认值为 MEDIUM。

*materialLocation*

一个 SymbolicConstant，指示材料是在 *referenceInstance* 内部还是外部。可能的值为 INSIDE 或 OUTSIDE。默认值为 INSIDE。

*description*

一个 String，指定场的描述。默认值为空字符串。

*scaleFactor*

一个 Float，指定被 *referenceInstance* 占据的体积分数。有效值为 0 到 1 之间。

**返回值**

一个 DiscreteField 对象。

**异常**

AbaqusException。

### 21.4.3 DiscreteFieldFromAnalytic(...)

此方法从 [AnalyticalField](pt01ch21pyo02.md) 对象创建 DiscreteField 对象。

**路径**

```
mdb.models[*name*].DiscreteFieldFromAnalytic
```

**必需参数**

*name*

一个 String，指定存储库键。

*location*

一个 SymbolicConstant 或一个 Int，指定域数据的位置。可能的值为 NODES 和 ELEMENTS。默认值为 NODES。

*analyticFieldName*

一个 String，指定包含源数据的 [AnalyticalField](pt01ch21pyo02.md) 名称。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定场所在的区域。

**可选参数**

无。

**返回值**

一个 DiscreteField 对象。

**异常**

AbaqusException。

### 21.4.4 setValues(...)

此方法修改 DiscreteField 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DiscreteField](pt01ch21pyo04.md#ker-discretefield-discretefield-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 21.4.5 成员

DiscreteField 对象具有与 [DiscreteField](pt01ch21pyo04.md#ker-discretefield-discretefield-pyc) 方法的参数相同的名称和描述的成员。





