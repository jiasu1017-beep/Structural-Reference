# 29.73 Ornl 对象

Ornl 对象指定由橡树岭国家实验室开发的本构模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].creep.ornl
mdb.models[*name*].materials[*name*].plastic.ornl
import odbMaterial
session.odbs[*name*].materials[*name*].creep.ornl
session.odbs[*name*].materials[*name*].plastic.ornl
```

### 29.73.1 Ornl(...)

此方法创建 Ornl 对象。

**路径**

```
mdb.models[*name*].materials[*name*].creep.Ornl
mdb.models[*name*].materials[*name*].plastic.Ornl
session.odbs[*name*].materials[*name*].creep.Ornl
session.odbs[*name*].materials[*name*].plastic.Ornl
```

**必需参数**

无。

**可选参数**

*a*

Float，指定由蠕变应变引起的运动偏移的饱和率，如核标准第 4.3.3-3 节方程（15）所定义。默认值为该标准的相应值。设置 *a*=0.0 以使用 1986 年修订版标准。默认值为 0.3。

*h*

`None` 或 Float，指定相对于蠕变应变的运动偏移率 [核标准第 4.3.2-1 节方程（7）]。如果 *h*=`None`，则根据 1981 年修订版标准的第 4.3.3-3 节确定 *h* 的值。设置 *h*=0.0 以使用 1986 年修订版标准。默认值为 `None`。

*reset*

Boolean，指定是否调用核标准第 4.3.5 节中描述的可选 ![](../graphics/ker_eqn00090.gif) 重置程序。默认值为 OFF。

**返回值**

Ornl 对象。

**异常**

RangeError。

### 29.73.2 setValues(...)

此方法修改 Ornl 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Ornl](pt01ch29pyo73.md#ker-ornl-ornl-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.73.3 成员

Ornl 对象的成员与 [Ornl](pt01ch29pyo73.md#ker-ornl-ornl-pyc) 方法的参数具有相同的名称和描述。

### 29.73.4 对应的分析关键字

| [*ORNL](../key/key-link.md#usb-kws-mornl) |
| --- |
