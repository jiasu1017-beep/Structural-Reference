# 29.50 FailStrain 对象

FailStrain 对象定义基于应变的失效度量参数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].elastic.failStrain
import odbMaterial
session.odbs[*name*].materials[*name*].elastic.failStrain
```

### 29.50.1 FailStrain(...)

此方法创建 FailStrain 对象。

**路径**

```
mdb.models[*name*].materials[*name*].elastic.FailStrain
session.odbs[*name*].materials[*name*].elastic.FailStrain
```

**必需参数**

*table*

 Float 元组序列，指定下述项目。

**可选参数**

*temperatureDependency*

 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

- 纤维方向拉伸应变极限，![](../graphics/ker_eqn00246.gif)。
- 纤维方向压缩应变极限，![](../graphics/ker_eqn00247.gif)。
- 横向拉伸应变极限，![](../graphics/ker_eqn00248.gif)。
- 横向压缩应变极限，![](../graphics/ker_eqn00249.gif)。
- ![](../graphics/ker_eqn00083.gif)--![](../graphics/ker_eqn00084.gif) 平面中的剪切应变极限，![](../graphics/ker_eqn00250.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

 FailStrain 对象。

**异常**

 RangeError。

### 29.50.2 setValues(...)

此方法修改 FailStrain 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [FailStrain](pt01ch29pyo50.md#ker-failstrain-failstrain-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.50.3 成员

FailStrain 对象的成员与 [FailStrain](pt01ch29pyo50.md#ker-failstrain-failstrain-pyc) 方法的参数具有相同的名称和描述。

### 29.50.4 对应的分析关键字

| [*FAIL STRAIN](../key/key-link.md#usb-kws-mefailstrain) |
| --- |
