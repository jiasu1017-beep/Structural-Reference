# 29.10 CapHardening 对象





CapHardening 对象指定 Drucker-Prager/帽盖塑性硬化。

**访问**

```
import material
mdb.models[*name*].materials[*name*].capPlasticity.capHardening
import odbMaterial
session.odbs[*name*].materials[*name*].capPlasticity.capHardening
```

### 29.10.1 CapHardening(...)

此方法创建 CapHardening 对象。

**路径**

```
mdb.models[*name*].materials[*name*].capPlasticity.CapHardening
session.odbs[*name*].materials[*name*].capPlasticity.CapHardening
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

**表格数据**

- 静水压力屈服应力。
- 对应体积非弹性应变的绝对值。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CapHardening 对象。

**异常**

RangeError。

### 29.10.2 setValues(...)

此方法修改 CapHardening 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CapHardening](pt01ch29pyo10.md#ker-caphardening-caphardening-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.10.3 成员

CapHardening 对象具有与 [CapHardening](pt01ch29pyo10.md#ker-caphardening-caphardening-pyc) 方法参数同名的成员，描述也相同。

### 29.10.4 对应的分析关键字

| [*CAP HARDENING](../key/key-link.md#usb-kws-mcaphardening) |
| --- |




