# 29.9 CapCreepConsolidation 对象





CapCreepConsolidation 对象指定帽盖蠕变模型和材料特性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].capPlasticity.capCreepConsolidation
import odbMaterial
session.odbs[*name*].materials[*name*].capPlasticity.capCreepConsolidation
```

### 29.9.1 CapCreepConsolidation(...)

此方法创建 CapCreepConsolidation 对象。

**路径**

```
mdb.models[*name*].materials[*name*].capPlasticity.CapCreepConsolidation
session.odbs[*name*].materials[*name*].capPlasticity.CapCreepConsolidation
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*law*

一个 SymbolicConstant，指定帽盖蠕变规律。可能的值为 STRAIN、TIME、SINGHM 和 USER。默认值为 STRAIN。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**表格数据**

如果 *law*=STRAIN 或 *law*=TIME，表格数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。
- ![](../graphics/ker_eqn00088.gif)。
- ![](../graphics/ker_eqn00089.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *law*=SINGHM，表格数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。
- ![](../graphics/ker_eqn00090.gif)。
- ![](../graphics/ker_eqn00089.gif)。
- ![](../graphics/ker_eqn00091.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CapCreepConsolidation 对象。

**异常**

无。

### 29.9.2 setValues(...)

此方法修改 CapCreepConsolidation 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CapCreepConsolidation](pt01ch29pyo09.md#ker-capcreepconsolidation-capcreepconsolidation-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.9.3 成员

CapCreepConsolidation 对象具有与 [CapCreepConsolidation](pt01ch29pyo09.md#ker-capcreepconsolidation-capcreepconsolidation-pyc) 方法参数同名的成员，描述也相同。

### 29.9.4 对应的分析关键字

| [*CAP CREEP](../key/key-link.md#usb-kws-mcapcreep) |
| --- |




