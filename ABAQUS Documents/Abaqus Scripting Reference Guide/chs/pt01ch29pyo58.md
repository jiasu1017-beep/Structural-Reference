# 29.58 Gel 对象

Gel 对象定义膨胀凝胶。

**访问**

```
import material
mdb.models[*name*].materials[*name*].gel
import odbMaterial
session.odbs[*name*].materials[*name*].gel
```

### 29.58.1 Gel(...)

此方法创建 Gel 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Gel
session.odbs[*name*].materials[*name*].Gel
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

无。

**表格数据**

- 完全干燥时凝胶颗粒的半径，![](../graphics/ker_eqn00259.gif)。
- 完全膨胀时凝胶颗粒的半径，![](../graphics/ker_eqn00260.gif)。
- 单位体积内凝胶颗粒的数量，![](../graphics/ker_eqn00261.gif)。
- 凝胶颗粒长期膨胀的松弛时间常数，![](../graphics/ker_eqn00262.gif)。

**返回值**

Gel 对象。

**异常**

无。

### 29.58.2 setValues(...)

此方法修改 Gel 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Gel](pt01ch29pyo58.md#ker-gel-gel-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.58.3 成员

Gel 对象的成员与 [Gel](pt01ch29pyo58.md#ker-gel-gel-pyc) 方法的参数具有相同的名称和描述。

### 29.58.4 对应的分析关键字

| [*GEL](../key/key-link.md#usb-kws-mgel) |
| --- |
