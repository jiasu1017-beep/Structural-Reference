# 29.84 PressureEffect 对象

PressureEffect 对象定义等效压力应力驱动的质量扩散。

**访问**

```
import material
mdb.models[*name*].materials[*name*].diffusivity.pressureEffect
import odbMaterial
session.odbs[*name*].materials[*name*].diffusivity.pressureEffect
```

### 29.84.1 PressureEffect(...)

此方法创建 PressureEffect 对象。

**路径**

```
mdb.models[*name*].materials[*name*].diffusivity.PressureEffect
session.odbs[*name*].materials[*name*].diffusivity.PressureEffect
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

- 压力应力因子，![](../graphics/ker_eqn00356.gif)。
- 浓度。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

PressureEffect 对象。

**异常**

RangeError。

### 29.84.2 setValues(...)

此方法修改 PressureEffect 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [PressureEffect](pt01ch29pyo84.md#ker-pressureeffect-pressureeffect-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.84.3 成员

PressureEffect 对象的成员与 [PressureEffect](pt01ch29pyo84.md#ker-pressureeffect-pressureeffect-pyc) 方法的参数具有相同的名称和描述。

### 29.84.4 对应的分析关键字

| [*KAPPA](../key/key-link.md#usb-kws-mkappa) |
| --- |
