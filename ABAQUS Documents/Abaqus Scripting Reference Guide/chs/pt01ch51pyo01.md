# 51.1 DiagnosticPrint 对象

DiagnosticPrint 对象用于请求详细的诊断输出或禁用特定的诊断检查。

**访问**

```
import step
mdb.models[*name*].steps[*name*].diagnosticPrint
```

### 51.1.1 DiagnosticPrint(...)

此方法创建一个 DiagnosticPrint 对象。

**路径**

```
mdb.models[*name*].steps[*name*].DiagnosticPrint
```

**必要参数**

无。

**可选参数**

*allke*

一个 Boolean，指定是否请求包含总动能的列。此参数仅对 Abaqus/Explicit 分析有效。默认值为 ON。

*criticalElement*

一个 Boolean，指定是否请求包含最小稳定时间增量的单元的列以及列出该值的列。此参数仅对 Abaqus/Explicit 分析有效。默认值为 ON。

*dmass*

一个 Boolean，指定是否请求包含由于质量缩放导致的模型总质量变化百分比的列。此参数仅对 Abaqus/Explicit 分析有效。除非模型中存在质量缩放，否则默认值为 OFF。

*etotal*

一个 Boolean，指定是否请求包含模型能量平衡的列。此参数仅对 Abaqus/Explicit 分析有效。默认值为 OFF。

*contact*

一个 Boolean，指定是否请求界面和间隙问题中接触或分离点的详细输出。此参数仅对 Abaqus/Standard 分析有效。默认值为 ON。

*modelChange*

一个 Boolean，指定是否请求在步骤中被移除或重新激活的单元的详细输出。此参数仅对 Abaqus/Standard 分析有效。默认值为 OFF。

*plasticity*

一个 Boolean，指定是否请求材料例程中塑性算法未能收敛的单元和积分点编号的详细输出。此参数仅对 Abaqus/Standard 分析有效。默认值为 OFF。

*residual*

一个 Boolean，指定是否在平衡迭代期间输出平衡残差。此参数仅对 Abaqus/Standard 分析有效。默认值为 ON。

*frequency*

一个 Int，指定输出频率（以增量计）。默认值为 1。

*solve*

一个 Boolean，指定是否请求每次迭代中实际方程数量和波前的相关信息。此参数仅对 Abaqus/Standard 分析有效。默认值为 ON。

*mass*

一个 Boolean，指定是否请求包含由于质量缩放导致的模型总质量的列。此参数仅对 Abaqus/Explicit 分析有效。默认值为 OFF。

**返回的值**

一个 DiagnosticPrint 对象。

**异常**

无。

### 51.1.2 setValues(...)

此方法修改 DiagnosticPrint 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [DiagnosticPrint](pt01ch51pyo01.md#ker-diagnosticprint-diagnosticprint-pyc) 方法的参数相同。

**返回的值**

无。

**异常**

无。

### 51.1.3 成员

DiagnosticPrint 对象的成员与 [DiagnosticPrint](pt01ch51pyo01.md#ker-diagnosticprint-diagnosticprint-pyc) 方法的参数具有相同的名称和描述。

### 51.1.4 对应的分析关键字

| [*DIAGNOSTICS](../key/key-link.md#usb-kws-hdiagnostics) |
| --- |
