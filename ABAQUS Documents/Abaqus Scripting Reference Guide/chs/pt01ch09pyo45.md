# 9.45 TypeBC 对象

TypeBC 对象存储应力/位移分析中常用的几种预定义边界条件类型的数据。

TypeBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.45.1 EncastreBC(...)

此方法创建 encastre TypeBC 对象。

**路径**

```
mdb.models[*name*].EncastreBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

**返回值**

TypeBC 对象。

**异常**

无。

### 9.45.2 PinnedBC(...)

此方法创建 pinned TypeBC 对象。

**路径**

```
mdb.models[*name*].PinnedBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

**返回值**

TypeBC 对象。

**异常**

无。

### 9.45.3 XsymmBC(...)

此方法创建指定关于 *X* 轴对称的 TypeBC 对象。

**路径**

```
mdb.models[*name*].XsymmBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

**返回值**

TypeBC 对象。

**异常**

无。

### 9.45.4 YsymmBC(...)

此方法创建指定关于 *Y* 轴对称的 TypeBC 对象。

**路径**

```
mdb.models[*name*].YsymmBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

**返回值**

TypeBC 对象。

**异常**

无。

### 9.45.5 ZsymmBC(...)

此方法创建指定关于 *Z* 轴对称的 TypeBC 对象。

**路径**

```
mdb.models[*name*].ZsymmBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

**返回值**

TypeBC 对象。

**异常**

无。

### 9.45.6 XasymmBC(...)

此方法创建指定关于 *X* 轴反对称的 TypeBC 对象。

**路径**

```
mdb.models[*name*].XasymmBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

**返回值**

TypeBC 对象。

**异常**

无。

### 9.45.7 YasmmmBC(...)

此方法创建指定关于 *Y* 轴反对称的 TypeBC 对象。

**路径**

```
mdb.models[*name*].YasymmBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

**返回值**

TypeBC 对象。

**异常**

无。

### 9.45.8 ZasymmBC(...)

此方法创建指定关于 *Z* 轴反对称的 TypeBC 对象。

**路径**

```
mdb.models[*name*].ZasymmBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

**返回值**

TypeBC 对象。

**异常**

无。

### 9.45.9 setValues(...)

此方法修改创建该对象的步骤中现有 TypeBC 对象的数据。

**必需参数**

无。

**可选参数**

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*typeName*

SymbolicConstant，指定预定义边界条件类型。可能的值为 XSYMM、YSYMM、ZSYMM、XASYMM、YASYMM、ZASYMM、PINNED 和 ENCASTRE。

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

**返回值**

无。

**异常**

无。

### 9.45.10 setValuesInStep(...)

此方法始终返回 TypeBC 的值错误；它是从 [BoundaryCondition](pt01ch09pyo01.md) 对象继承的。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*typeName*

SymbolicConstant，指定预定义边界条件类型。可能的值为 XSYMM、YSYMM、ZSYMM、XASYMM、YASYMM、ZASYMM、PINNED 和 ENCASTRE。

**返回值**

无。

**异常**

值错误：

```
对称/反对称/固定边界条件不能在传播步骤中编辑。
```

### 9.45.11 成员

TypeBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*category*

SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
