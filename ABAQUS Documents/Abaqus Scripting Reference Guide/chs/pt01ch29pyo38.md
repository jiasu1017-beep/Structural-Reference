# 29.38 Depvar 对象





Depvar 对象指定依赖于解的状态变量。

**访问**

```
import material
mdb.models[*name*].materials[*name*].depvar
import odbMaterial
session.odbs[*name*].materials[*name*].depvar
```

### 29.38.1 Depvar(...)

此方法创建 Depvar 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Depvar
session.odbs[*name*].materials[*name*].Depvar
```

**必需参数**

无。

**可选参数**

*deleteVar*

一个 Int，指定控制单元删除标志的状态变量编号。默认值为 0。

此参数仅适用于 Abaqus/Explicit 分析。

*n*

一个 Int，指定每个积分点所需的依赖于解的状态变量的数量。默认值为 0。

**返回值**

一个 Depvar 对象。

**异常**

RangeError。

### 29.38.2 setValues(...)

此方法修改 Depvar 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Depvar](pt01ch29pyo38.md#ker-depvar-depvar-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.38.3 成员

Depvar 对象具有与 [Depvar](pt01ch29pyo38.md#ker-depvar-depvar-pyc) 方法参数同名的成员，描述也相同。

### 29.38.4 对应的分析关键字

| [*DEPVAR](../key/key-link.md#usb-kws-mdepvar) |
| --- |




