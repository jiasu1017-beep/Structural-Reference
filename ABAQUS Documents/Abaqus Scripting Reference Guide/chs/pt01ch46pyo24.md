# 46.24 TransverseShearBeam 对象





TransverseShearBeam 对象定义梁截面横向剪切刚度属性。

**访问**

```
import section
mdb.models[*name*].sections[*name*].beamTransverseShear
import odbSection
session.odbs[*name*].sections[*name*].beamTransverseShear
```

### 46.24.1 TransverseShearBeam(...)

此方法创建 TransverseShearBeam 对象。

**路径**

```
mdb.models[*name*].sections[*name*].TransverseShearBeam
session.odbs[*name*].sections[*name*].TransverseShearBeam
```

**必要参数**

*scfDefinition*

SymbolicConstant，指定如何给出截面细长比补偿因子。可能的值为 ANALYSIS_DEFAULT、COMPUTED 和 VALUE。

**可选参数**

*k23*

 `None` 或 Float，指定截面的 k23 剪切刚度。默认值为 `None`。

*k13*

 `None` 或 Float，指定截面的 k13 剪切刚度。默认值为 `None`。

*slendernessCompensation*

SymbolicConstant COMPUTED 或 Float，指定截面的细长比补偿因子。默认值为 0.25。

**返回值**

TransverseShearBeam 对象。

**异常**

无。

### 46.24.2 setValues(...)

此方法修改 TransverseShearBeam 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [TransverseShearBeam](pt01ch46pyo24.md#ker-transverseshearbeam-transverseshearbeam-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 46.24.3 成员

TransverseShearBeam 对象的成员与 [TransverseShearBeam](pt01ch46pyo24.md#ker-transverseshearbeam-transverseshearbeam-pyc) 方法的参数具有相同的名称和描述。

### 46.24.4 对应分析关键字

| [*TRANSVERSE SHEAR STIFFNESS](../key/key-link.md#usb-kws-mtransshearstiff) |
| --- |


