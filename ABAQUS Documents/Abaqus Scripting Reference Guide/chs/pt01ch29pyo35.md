# 29.35 Damping 对象





Damping 对象指定材料阻尼。

**访问**

```
import material
mdb.models[*name*].materials[*name*].damping
import odbMaterial
session.odbs[*name*].materials[*name*].damping
```

### 29.35.1 Damping(...)

此方法创建 Damping 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Damping
session.odbs[*name*].materials[*name*].Damping
```

**必需参数**

无。

**可选参数**

*alpha*

一个 Float，指定 ![](../graphics/ker_eqn00161.gif) 因子，用于在直接积分和显式动力学中创建质量比例阻尼。默认值为 0.0。

*beta*

一个 Float，指定 ![](../graphics/ker_eqn00162.gif) 因子，用于在直接积分和显式动力学中创建刚度比例阻尼。默认值为 0.0。

*composite*

一个 Float，指定临界阻尼比，在计算模态动力学中用于此材料的复合阻尼因子时使用。默认值为 0.0。

此参数仅适用于 Abaqus/Standard 分析。

*structural*

一个 Float，指定结构因子，用于在直接积分和显式动力学中创建材料阻尼。默认值为 0.0。

**返回值**

一个 Damping 对象。

**异常**

RangeError。

### 29.35.2 setValues(...)

此方法修改 Damping 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Damping](pt01ch29pyo35.md#ker-damping-damping-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.35.3 成员

Damping 对象具有与 [Damping](pt01ch29pyo35.md#ker-damping-damping-pyc) 方法参数同名的成员，描述也相同。

### 29.35.4 对应的分析关键字

| [*DAMPING](../key/key-link.md#usb-kws-mdamping) |
| --- |




