# 25.18 ContactDamping 对象

ContactDamping 对象为接触交互属性指定阻尼。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].damping
```

### 25.18.1 Damping(...)

此方法创建一个 ContactDamping 对象。

**路径**

```
mdb.models[*name*].interactionProperties[*name*].Damping
```

**必需参数**

无。

**可选参数**

*definition*

 SymbolicConstant，指定用于定义阻尼的方法。可能的值为 DAMPING_COEFFICIENT 和 CRITICAL_DAMPING_FRACTION。默认值为 DAMPING_COEFFICIENT。

*tangentFraction*

 SymbolicConstant DEFAULT 或浮点数，指定切向阻尼系数与法向阻尼系数的比值。默认值为 DEFAULT。

*clearanceDependence*

 SymbolicConstant，指定阻尼系数或分数相对于间隙的变化。可能的值为 STEP、LINEAR 和 BILINEAR。默认值为 STEP。

如果 *definition*=CRITICAL_DAMPING_FRACTION，唯一的可能值为 STEP。

*table*

浮点数对的序列，指定阻尼属性。表格数据中的项目在下面描述。

**表格数据**

如果 *definition*=DAMPING_COEFFICIENT 且 *clearanceDependence*=STEP，表格数据指定以下内容：
- 阻尼系数。

如果 *definition*=DAMPING_COEFFICIENT 且 *clearanceDependence*=LINEAR 或 BILINEAR，表格数据指定以下内容：
- 阻尼系数。
- 间隙。

对于 *clearanceDependence*=LINEAR 必须给出两对，对于 *clearanceDependence*=BILINEAR 必须给出三对。第一对的 *clearance*=0.0，最后一对的 *coefficient*=0.0。

如果 *definition*=CRITICAL_DAMPING_FRACTION，表格数据指定以下内容：
- 临界阻尼分数。

**返回值**

ContactDamping 对象。

**异常**

无。

### 25.18.2 setValues(...)

此方法修改 ContactDamping 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ContactDamping](pt01ch25pyo18.md#ker-contactdamping-damping-pyc) 方法的参数相同。

**返回值**

无。

**异常**

无。

### 25.18.3 成员

ContactDamping 对象具有以下成员：

*definition*

 SymbolicConstant，指定用于定义阻尼的方法。可能的值为 DAMPING_COEFFICIENT 和 CRITICAL_DAMPING_FRACTION。默认值为 DAMPING_COEFFICIENT。

*tangentFraction*

 SymbolicConstant DEFAULT 或浮点数，指定切向阻尼系数与法向阻尼系数的比值。默认值为 DEFAULT。

*clearanceDependence*

 SymbolicConstant，指定阻尼系数或分数相对于间隙的变化。可能的值为 STEP、LINEAR 和 BILINEAR。默认值为 STEP。

如果 *definition*=CRITICAL_DAMPING_FRACTION，唯一的可能值为 STEP。

*table*

浮点数对的元组，指定阻尼属性。表格数据中的项目在下面描述。

### 25.18.4 对应的分析关键字

| [*CONTACT DAMPING](../key/key-link.md#usb-kws-hcontactdamping) |
| --- |



