# 29.25 ContactArea 对象





ContactArea 对象在 GasketThicknessBehavior 对象的 *variableUnits*=FORCE 时指定垫片厚度行为的子选项。ContactArea 对象定义接触面积或接触宽度与闭合曲线，以通过变量 CS11 输出平均压力。

**访问**

```
import material
mdb.models[*name*].materials[*name*].gasketThicknessBehavior.contactArea
import odbMaterial
session.odbs[*name*].materials[*name*].gasketThicknessBehavior.contactArea
```

### 29.25.1 ContactArea(...)

此方法创建 ContactArea 对象。

**路径**

```
mdb.models[*name*].materials[*name*].gasketThicknessBehavior.ContactArea
session.odbs[*name*].materials[*name*].gasketThicknessBehavior.ContactArea
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个 Boolean，指定接触面积数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定接触面积数据定义中包含的场变量依赖数量（除温度外）。默认值为 0。

**表格数据**

- 接触面积或宽度；此值必须为正。
- 闭合量；此值必须为正。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 ContactArea 对象。

**异常**

无。

### 29.25.2 setValues(...)

此方法修改 ContactArea 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ContactArea](pt01ch29pyo25.md#ker-contactarea-contactarea-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.25.3 成员

ContactArea 对象具有与 [ContactArea](pt01ch29pyo25.md#ker-contactarea-contactarea-pyc) 方法参数同名的成员，描述也相同。

### 29.25.4 对应的分析关键字

| [*GASKET CONTACT AREA](../key/key-link.md#usb-kws-mgasketcontactarea) |
| --- |




