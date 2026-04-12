# 29.55 GasketMembraneElastic 对象

GasketMembraneElastic 对象定义垫片膜剪切行为的弹性参数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].gasketMembraneElastic
import odbMaterial
session.odbs[*name*].materials[*name*].gasketMembraneElastic
```

### 29.55.1 GasketMembraneElastic(...)

此方法创建 GasketMembraneElastic 对象。

**路径**

```
mdb.models[*name*].materials[*name*].GasketMembraneElastic
session.odbs[*name*].materials[*name*].GasketMembraneElastic
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

- 杨氏模量，![](../graphics/ker_eqn00163.gif)。
- 泊松比，![](../graphics/ker_eqn00164.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

 GasketMembraneElastic 对象。

**异常**

 RangeError。

### 29.55.2 setValues(...)

此方法修改 GasketMembraneElastic 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [GasketMembraneElastic](pt01ch29pyo55.md#ker-gasketmembraneelastic-gasketmembraneelastic-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.55.3 成员

GasketMembraneElastic 对象的成员与 [GasketMembraneElastic](pt01ch29pyo55.md#ker-gasketmembraneelastic-gasketmembraneelastic-pyc) 方法的参数具有相同的名称和描述。

### 29.55.4 对应的分析关键字

| [*GASKET ELASTICITY](../key/key-link.md#usb-kws-mgasketelastic) |
| --- |
