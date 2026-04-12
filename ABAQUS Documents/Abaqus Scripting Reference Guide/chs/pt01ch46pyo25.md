# 46.25 TransverseShearShell 对象





TransverseShearShell 对象定义壳截面横向剪切刚度属性。

**访问**

```
import section
mdb.models[*name*].sections[*name*].transverseShear
import odbSection
session.odbs[*name*].sections[*name*].transverseShear
```

### 46.25.1 TransverseShearShell(...)

此方法创建 TransverseShearShell 对象。

**路径**

```
mdb.models[*name*].sections[*name*].TransverseShearShell
session.odbs[*name*].sections[*name*].TransverseShearShell
```

**必要参数**

*k11*

Float，指定第一个方向上截面的剪切刚度。

*k22*

Float，指定第二个方向上截面的剪切刚度。

*k12*

Float，指定截面剪切刚度中的耦合项。

**可选参数**

无。

**返回值**

TransverseShearShell 对象。

**异常**

无。

### 46.25.2 setValues(...)

此方法修改 TransverseShearShell 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [TransverseShearShell](pt01ch46pyo25.md#ker-transverseshearshell-transverseshearshell-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 46.25.3 成员

TransverseShearShell 对象的成员与 [TransverseShearShell](pt01ch46pyo25.md#ker-transverseshearshell-transverseshearshell-pyc) 方法的参数具有相同的名称和描述。

### 46.25.4 对应分析关键字

| [*TRANSVERSE SHEAR STIFFNESS](../key/key-link.md#usb-kws-mtransshearstiff) |
| --- |


