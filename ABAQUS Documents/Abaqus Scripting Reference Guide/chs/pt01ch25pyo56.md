# 25.56 Radiation 对象

Radiation 对象为接触交互属性指定辐射。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].radiation
```

### 25.56.1 Radiation(...)

此方法创建一个 Radiation 对象。

**路径**

```
mdb.models[*name*].interactionProperties[*name*].Radiation
```

**必需参数**

*masterEmissivity*

浮点数，指定主表面的发射率。

*slaveEmissivity*

浮点数，指定从属表面的发射率。

*table*

浮点数序列的序列，指定以下内容：
- 有效视角因子，![](../graphics/ker_eqn00081.gif)。
- 间隙清除，![](../graphics/ker_eqn00082.gif)。

**可选参数**

无。

**返回值**

Radiation 对象。

**异常**

无。

### 25.56.2 setValues(...)

此方法修改 Radiation 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Radiation](pt01ch25pyo56.md#ker-radiation-radiation-pyc) 方法的参数相同。

**返回值**

无。

**异常**

无。

### 25.56.3 成员

Radiation 对象的成员与 [Radiation](pt01ch25pyo56.md#ker-radiation-radiation-pyc) 方法的参数具有相同的名称和描述。

### 25.56.4 对应的分析关键字

| [*GAP RADIATION](../key/key-link.md#usb-kws-mgapradiation) |
| --- |



