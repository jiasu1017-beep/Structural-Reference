# 29.62 Hypoelastic 对象

Hypoelastic 对象指定超弹性材料属性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].hypoelastic
import odbMaterial
session.odbs[*name*].materials[*name*].hypoelastic
```

### 29.62.1 Hypoelastic(...)

此方法创建 Hypoelastic 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Hypoelastic
session.odbs[*name*].materials[*name*].Hypoelastic
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*user*

Boolean，指定通过用户子程序 [`UHYPEL`](../sub/sub-link.md#sub-xsl-uhypel) 定义超弹性。默认值为 OFF。

**表格数据**

- 瞬时杨氏模量，![](../graphics/ker_eqn00163.gif)。
- 瞬时泊松比，![](../graphics/ker_eqn00164.gif)。
- 第一应变不变量，![](../graphics/ker_eqn00285.gif)。
- 第二应变不变量，![](../graphics/ker_eqn00286.gif)。
- 第三应变不变量，![](../graphics/ker_eqn00287.gif)。

**返回值**

Hypoelastic 对象。

**异常**

无。

### 29.62.2 setValues(...)

此方法修改 Hypoelastic 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Hypoelastic](pt01ch29pyo62.md#ker-hypoelastic-hypoelastic-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.62.3 成员

Hypoelastic 对象的成员与 [Hypoelastic](pt01ch29pyo62.md#ker-hypoelastic-hypoelastic-pyc) 方法的参数具有相同的名称和描述。

### 29.62.4 对应的分析关键字

| [*HYPOELASTIC](../key/key-link.md#usb-kws-mhypoelastic) |
| --- |
