# 29.54 GapFlow 对象

GapFlow 对象为孔隙压力相干元素指定切向流动本构参数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].gapFlow
import odbMaterial
session.odbs[*name*].materials[*name*].gapFlow
```

### 29.54.1 GapFlow(...)

此方法创建 GapFlow 对象。

**路径**

```
mdb.models[*name*].materials[*name*].GapFlow
session.odbs[*name*].materials[*name*].GapFlow
```

**必需参数**

*table*

 Float 元组序列，指定下述项目。

**可选参数**

*kmax*

 `None` 或 Float，指定应使用的最大渗透率值。如果 *kmax*=`None`，Abaqus 假定渗透率无界。此值仅在 *type*=NEWTONIAN 时有意义。默认值为 `None`。

*temperatureDependency*

 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

*type*

 SymbolicConstant，指定间隙流动类型。可能的值为 NEWTONIAN 和 POWER_LAW。默认值为 NEWTONIAN。

**表格数据**

如果 *type*=NEWTONIAN，表格数据指定以下内容：
- 孔隙粘度。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=POWER_LAW，表格数据指定以下内容：
- 稠度。
- 指数。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

 GapFlow 对象。

**异常**

无。

### 29.54.2 setValues(...)

此方法修改 GapFlow 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [GapFlow](pt01ch29pyo54.md#ker-gapflow-gapflow-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.54.3 成员

GapFlow 对象的成员与 [GapFlow](pt01ch29pyo54.md#ker-gapflow-gapflow-pyc) 方法的参数具有相同的名称和描述。

### 29.54.4 对应的分析关键字

| [*GAP FLOW](../key/key-link.md#usb-kws-mgapflow) |
| --- |
