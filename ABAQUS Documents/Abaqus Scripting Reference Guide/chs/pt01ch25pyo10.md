# 25.9 CavityRadiationProp 对象

CavityRadiationProp 对象是交互属性，定义作为温度和场变量函数的发射率。

CavityRadiationProp 对象派生自 [InteractionProperty](pt01ch25pyo48.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.9.1 CavityRadiationProp(...)

此方法创建一个 CavityRadiationProp 对象。

**路径**

```
mdb.models[*name*].CavityRadiationProp
```

**必需参数**

*name*

字符串，指定交互属性存储库键。

**可选参数**

*temperatureDependency*

布尔值，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

整数，指定场变量依赖项的数量。默认值为 0。

*property*

浮点数序列的序列，指定以下内容：
- 发射率，![](../graphics/ker_eqn00062.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

CavityRadiationProp 对象。

**异常**

无。

### 25.9.2 setValues(...)

此方法修改 CavityRadiationProp 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CavityRadiationProp](pt01ch25pyo09.md#ker-cavityradiationprop-cavityradiationprop-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 25.9.3 成员

CavityRadiationProp 对象的成员与 [CavityRadiationProp](pt01ch25pyo09.md#ker-cavityradiationprop-cavityradiationprop-pyc) 方法的参数具有相同的名称和描述。

### 25.9.4 对应的分析关键字

| [*EMISSIVITY](../key/key-link.md#usb-kws-memissivity) |
| --- |



