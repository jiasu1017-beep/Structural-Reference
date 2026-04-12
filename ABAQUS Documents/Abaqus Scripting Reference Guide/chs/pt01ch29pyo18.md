# 29.18 Concrete 对象





Concrete 对象定义超出弹性范围的混凝土特性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].concrete
import odbMaterial
session.odbs[*name*].materials[*name*].concrete
```

### 29.18.1 Concrete(...)

此方法创建 Concrete 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Concrete
session.odbs[*name*].materials[*name*].Concrete
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

- 压应力绝对值。
- 塑性应变绝对值。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 Concrete 对象。

**异常**

RangeError。

### 29.18.2 setValues(...)

此方法修改 Concrete 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Concrete](pt01ch29pyo18.md#ker-concrete-concrete-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.18.3 成员

Concrete 对象具有与 [Concrete](pt01ch29pyo18.md#ker-concrete-concrete-pyc) 方法参数同名的成员，描述也相同。

此外，Concrete 对象可以具有以下成员：

*failureRatios*

一个 [FailureRatios](pt01ch29pyo52.md) 对象。

*shearRetention*

一个 [ShearRetention](pt01ch29pyo89.md) 对象。

*tensionStiffening*

一个 [TensionStiffening](pt01ch29pyo98.md) 对象。

### 29.18.4 对应的分析关键字

| [*CONCRETE](../key/key-link.md#usb-kws-mconcrete) |
| --- |




