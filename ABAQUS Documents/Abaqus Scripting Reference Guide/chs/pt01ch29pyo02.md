# 29.2 AcousticMedium 对象





AcousticMedium 对象指定材料的声学特性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].acousticMedium
import odbMaterial
session.odbs[*name*].materials[*name*].acousticMedium
```

### 29.2.1 AcousticMedium(...)

此方法创建 AcousticMedium 对象。

**路径**

```
mdb.models[*name*].materials[*name*].AcousticMedium
session.odbs[*name*].materials[*name*].AcousticMedium
```

**必需参数**

无。

**可选参数**

*acousticVolumetricDrag*

一个 Boolean，指定是否指定了 volumetricTable 数据。默认值为 OFF。

*temperatureDependencyB*

一个 Boolean，指定 *bulkTable* 中的数据是否依赖于温度。默认值为 OFF。

*temperatureDependencyV*

一个 Boolean，指定 *volumetricTable* 中的数据是否依赖于温度。默认值为 OFF。

*dependenciesB*

一个 Int，指定 *bulkTable* 中数据的场变量依赖数量。默认值为 0。

*dependenciesV*

一个 Int，指定 *volumetricTable* 中数据的场变量依赖数量。默认值为 0。

*bulkTable*

一个 Float 序列的序列，指定以下内容：
- 体积模量。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

默认值为空序列。

*volumetricTable*

一个 Float 序列的序列，指定以下内容：
- 体积阻力。
- 频率。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

默认值为空序列。

**返回值**

一个 AcousticMedium 对象。

**异常**

RangeError。

### 29.2.2 setValues(...)

此方法修改 AcousticMedium 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [AcousticMedium](pt01ch29pyo02.md#ker-acousticmedium-acousticmedium-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.2.3 成员

AcousticMedium 对象具有与 [AcousticMedium](pt01ch29pyo02.md#ker-acousticmedium-acousticmedium-pyc) 方法参数同名的成员，描述也相同。

### 29.2.4 对应的分析关键字

| [*ACOUSTIC MEDIUM](../key/key-link.md#usb-kws-macousticmed) |
| --- |




