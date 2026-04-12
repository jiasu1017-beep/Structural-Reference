# 25.52 ModelChange 对象

ModelChange 对象定义用于元素移除和重新激活的模型更改交互。

ModelChange 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.52.1 ModelChange(...)

此方法创建一个 ModelChange 对象。

**路径**

```
mdb.models[*name*].ModelChange
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 ModelChange 对象的步骤名称。

**可选参数**

*isRestart*

布尔值，指定此交互是否仅用于指示在后续重启分析中可能需要模型更改（无论是元素还是接触对）。默认值为 OFF。

*regionType*

 SymbolicConstant，指定区域选择类型。此参数仅在 *isRestart*=False 时有效。可能的值为 GEOMETRY、SKINS、STRINGERS 和 ELEMENTS。默认值为 GEOMETRY。

*region*

[Region](pt01ch45pyo03.md) 对象，指定要移除或重新激活的元素。此参数仅在 *isRestart*=False 时有效。

*activeInStep*

布尔值，指定元素是否正在被移除或重新激活。此参数仅在 *isRestart*=False 时有效。默认值为 OFF。

*includeStrain*

布尔值，指定是否使用应变重新激活应力/位移元素。此参数仅在 *isRestart*=False 且 *activeInStep*=True 时有效。默认值为 OFF。

**返回值**

ModelChange 对象。

**异常**

无。

### 25.52.2 setValues(...)

此方法修改创建 ModelChange 对象的步骤中现有 ModelChange 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ModelChange](pt01ch25pyo52.md#ker-modelchange-modelchange-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.52.3 setValuesInStep(...)

此方法修改指定步骤中现有 ModelChange 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

*activeInStep*

布尔值，指定元素是否正在被移除或重新激活。此参数仅在 *isRestart*=False 时有效。默认值为 OFF。

*includeStrain*

布尔值，指定是否使用应变重新激活应力/位移元素。此参数仅在 *isRestart*=False 且 *activeInStep*=True 时有效。默认值为 OFF。

**返回值**

无。

**异常**

无。

### 25.52.4 成员

ModelChange 对象的成员与 [ModelChange](pt01ch25pyo52.md#ker-modelchange-modelchange-pyc) 方法的参数具有相同的名称和描述。

### 25.52.5 对应的分析关键字

| [*MODEL CHANGE](../key/key-link.md#usb-kws-hmodelchange), TYPE=ELEMENT |
| --- |
| [*MODEL CHANGE](../key/key-link.md#usb-kws-hmodelchange), ACTIVATE |



