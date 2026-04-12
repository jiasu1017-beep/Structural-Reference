# 34.30 UserData 对象

UserData 对象包含用户定义的 XY 数据。UserData 对象没有构造函数；当创建 [Odb](pt01ch34pyo01.md) 对象时会自动创建它。

**访问**

```
import odbAccess
session.odbs[*name*].userData
```

### 34.30.1 XYData(...)

此方法从 *X–Y* 数据对序列创建 [XYData](pt01ch55pyo01.md) 对象。

**路径**

```
session.odbs[name].userData.XYData
```

**必要参数**

*name*

一个字符串，指定仓库键。

*data*

浮点数对序列，指定 *X–Y* 数据对。

**可选参数**

*sourceDescription*

一个字符串，指定 *X–Y* 数据的来源（例如，"从键盘输入"、"从 ASCII 文件获取"、"从 ODB 读取"等）。默认值为空字符串。

*contentDescription*

一个字符串，指定 *X–Y* 数据的内容（例如，"field 1 vs. field 2"）。默认值为空字符串。

*positionDescription*

一个字符串，指定 *X–Y* 数据的附加信息（例如，"for whole model"）。默认值为空字符串。

*legendLabel*

一个字符串，指定图例中使用的标签。默认值为 XYData 对象的名称。

*xValuesLabel*

一个字符串，指定 X 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能会被覆盖。默认值为空字符串。

*yValuesLabel*

一个字符串，指定 Y 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能会被覆盖。默认值为空字符串。

*axis1QuantityType*

一个 [QuantityType](pt01ch55pyo11.md) 对象，指定与 X-axis1 值关联的 [QuantityType](pt01ch55pyo11.md) 对象。

*axis2QuantityType*

一个 [QuantityType](pt01ch55pyo11.md) 对象，指定与 Y-axis2 值关联的 [QuantityType](pt01ch55pyo11.md) 对象。

**返回值**

[XYData](pt01ch55pyo01.md) 对象。

**异常**

InvalidNameError。

### 34.30.2 成员

UserData 对象可以具有以下成员：

*name*

一个字符串，指定仓库键。

*sourceDescription*

一个字符串，指定 *X–Y* 数据的来源（例如，"从键盘输入"、"从 ASCII 文件获取"、"从 ODB 读取"等）。默认值为空字符串。

*contentDescription*

一个字符串，指定 *X–Y* 数据的内容（例如，"field 1 vs. field 2"）。默认值为空字符串。

*positionDescription*

一个字符串，指定 *X–Y* 数据的附加信息（例如，"for whole model"）。默认值为空字符串。

*xValuesLabel*

一个字符串，指定 X 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能会被覆盖。默认值为空字符串。

*yValuesLabel*

一个字符串，指定 Y 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能会被覆盖。默认值为空字符串。

*axis1QuantityType*

一个 [QuantityType](pt01ch55pyo11.md) 对象，指定与 X-axis1 值关联的 [QuantityType](pt01ch55pyo11.md) 对象。

*axis2QuantityType*

一个 [QuantityType](pt01ch55pyo11.md) 对象，指定与 Y-axis2 值关联的 [QuantityType](pt01ch55pyo11.md) 对象。

*legendLabel*

一个字符串，指定图例中使用的标签。默认值为 XYData 对象的名称。

*xyDataObjects*

[XYData](pt01ch55pyo01.md) 对象的仓库。

*annotations*

[Annotation](pt01ch05pyo01.md) 对象的仓库。

*data*

浮点数对元组，指定 *X–Y* 数据对。
