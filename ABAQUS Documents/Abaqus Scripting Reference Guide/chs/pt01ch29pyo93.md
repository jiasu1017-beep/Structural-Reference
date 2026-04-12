# 29.93 SoretEffect 对象

SoretEffect 对象定义温度梯度驱动的质量扩散。

**访问**

```
import material
mdb.models[*name*].materials[*name*].diffusivity.soretEffect
import odbMaterial
session.odbs[*name*].materials[*name*].diffusivity.soretEffect
```

### 29.93.1 SoretEffect(...)

此方法创建 SoretEffect 对象。

**路径**

```
mdb.models[*name*].materials[*name*].diffusivity.SoretEffect
session.odbs[*name*].materials[*name*].diffusivity.SoretEffect
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

- Soret 效应因子，![](../graphics/ker_eqn00367.gif)。
- 浓度。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

SoretEffect 对象。

**异常**

RangeError。

### 29.93.2 setValues(...)

此方法修改 SoretEffect 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SoretEffect](pt01ch29pyo93.md#ker-soreteffect-soreteffect-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.93.3 成员

SoretEffect 对象的成员与 [SoretEffect](pt01ch29pyo93.md#ker-soreteffect-soreteffect-pyc) 方法的参数具有相同的名称和描述。

### 29.93.4 对应的分析关键字

| [*KAPPA](../key/key-link.md#usb-kws-mkappa) |
| --- |
