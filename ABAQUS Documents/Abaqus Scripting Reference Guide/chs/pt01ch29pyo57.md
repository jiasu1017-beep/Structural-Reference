# 29.57 GasketTransverseShearElastic 对象

GasketTransverseShearElastic 对象定义垫片横向剪切行为的弹性参数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].gasketTransverseShearElastic
import odbMaterial
session.odbs[*name*].materials[*name*].gasketTransverseShearElastic
```

### 29.57.1 GasketTransverseShearElastic(...)

此方法创建 GasketTransverseShearElastic 对象。

**路径**

```
mdb.models[*name*].materials[*name*].GasketTransverseShearElastic
session.odbs[*name*].materials[*name*].GasketTransverseShearElastic
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

*variableUnits*

SymbolicConstant，指定定义横向剪切行为的单位系统。可能的值为 STRESS 和 FORCE。默认值为 STRESS。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

- 剪切刚度。（此值不能为负。）
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

GasketTransverseShearElastic 对象。

**异常**

RangeError。

### 29.57.2 setValues(...)

此方法修改 GasketTransverseShearElastic 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [GasketTransverseShearElastic](pt01ch29pyo57.md#ker-gaskettransverseshearelastic-gaskettransverseshearel-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.57.3 成员

GasketTransverseShearElastic 对象的成员与 [GasketTransverseShearElastic](pt01ch29pyo57.md#ker-gaskettransverseshearelastic-gaskettransverseshearel-pyc) 方法的参数具有相同的名称和描述。

### 29.57.4 对应的分析关键字

| [*GASKET ELASTICITY](../key/key-link.md#usb-kws-mgasketelastic) |
| --- |
