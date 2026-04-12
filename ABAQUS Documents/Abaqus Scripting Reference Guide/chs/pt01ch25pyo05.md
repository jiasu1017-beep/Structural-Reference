# 25.3 AcousticImpedanceProp 对象

AcousticImpedanceProp 对象是交互属性，定义由 [AcousticImpedance](pt01ch25pyo02.md) 对象引用的属性。

AcousticImpedanceProp 对象派生自 [InteractionProperty](pt01ch25pyo48.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.3.1 AcousticImpedanceProp(...)

此方法创建一个 AcousticImpedanceProp 对象。

**路径**

```
mdb.models[*name*].AcousticImpedanceProp
```

**必需参数**

*name*

字符串，指定交互属性存储库键。

*tableType*

 SymbolicConstant，指定要定义的表格数据类型。可能的值为 IMPEDANCE 和 ADMITTANCE。

*table*

浮点数序列的序列，指定声阻抗属性。

如果 *tableType*=IMPEDANCE，表格数据的每个序列指定：
- 复阻抗的实部。
- 复阻抗的虚部。
- 频率（如果数据依赖于频率）。

如果 *tableType*=ADMITTANCE，表格数据的每个序列指定：
- 复导纳的实部。
- 复导纳的虚部。
- 频率（如果数据依赖于频率）。

**可选参数**

*frequencyDependency*

布尔值，指定 *table* 数据是否依赖于频率。默认值为 OFF。

**返回值**

AcousticImpedanceProp 对象。

**异常**

无。

### 25.3.2 setValues(...)

此方法修改 AcousticImpedanceProp 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [AcousticImpedanceProp](pt01ch25pyo03.md#ker-acousticimpedanceprop-acousticimpedanceprop-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 25.3.3 成员

AcousticImpedanceProp 对象的成员与 [AcousticImpedanceProp](pt01ch25pyo03.md#ker-acousticimpedanceprop-acousticimpedanceprop-pyc) 方法的参数具有相同的名称和描述。

### 25.3.4 对应的分析关键字

| [*IMPEDANCE PROPERTY](../key/key-link.md#usb-kws-mimpedanceprop) |
| --- |



