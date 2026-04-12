# 29.49 Expansion 对象

Expansion 对象指定热膨胀。

**访问**

```
import material
mdb.models[*name*].materials[*name*].expansion
import odbMaterial
session.odbs[*name*].materials[*name*].expansion
```

### 29.49.1 Expansion(...)

此方法创建 Expansion 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Expansion
session.odbs[*name*].materials[*name*].Expansion
```

**必需参数**

无。

**可选参数**

*type*

 SymbolicConstant，指定膨胀类型。可能的值为 ISOTROPIC、ORTHOTROPIC、ANISOTROPIC 和 SHORT_FIBER。默认值为 ISOTROPIC。

*userSubroutine*

 Boolean，指定是否使用用户子程序定义热应变增量。默认值为 OFF。

*zero*

 Float，指定 ![](../graphics/ker_eqn00061.gif) 的值（如果热膨胀依赖于温度或场变量）。默认值为 0.0。

*temperatureDependency*

 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

*table*

 Float 元组序列，指定下述项目。默认值为空序列。

仅在 *type* 不为 USER 时需要此参数。

**表格数据**

如果 *type*=ISOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00239.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=ORTHOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00240.gif)。
- ![](../graphics/ker_eqn00241.gif)。
- ![](../graphics/ker_eqn00242.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=ANISOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00240.gif)。
- ![](../graphics/ker_eqn00241.gif)。
- ![](../graphics/ker_eqn00242.gif)。（平面应力情况不使用。）
- ![](../graphics/ker_eqn00243.gif)。
- ![](../graphics/ker_eqn00244.gif)。
- ![](../graphics/ker_eqn00245.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=SHORT_FIBER，则没有表格数据。

**返回值**

 Expansion 对象。

**异常**

 RangeError。

### 29.49.2 setValues(...)

此方法修改 Expansion 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [Expansion](pt01ch29pyo49.md#ker-expansion-expansion-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.49.3 成员

Expansion 对象的成员与 [Expansion](pt01ch29pyo49.md#ker-expansion-expansion-pyc) 方法的参数具有相同的名称和描述。

### 29.49.4 对应的分析关键字

| [*EXPANSION](../key/key-link.md#usb-kws-mexpansion) |
| --- |
