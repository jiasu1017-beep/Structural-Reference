# 25.67 StdInitialization 对象

StdInitialization 对象与 Abaqus/Standard 分析中的 [ContactStd](pt01ch25pyo24.md) 结合使用来指定接触初始化数据。

StdInitialization 对象派生自 [ContactInitialization](pt01ch25pyo20.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].contactInitializations[*name*]
```

### 25.67.1 StdInitialization(...)

此方法创建一个 StdInitialization 对象。

**路径**

```
mdb.models[*name*].StdInitialization
```

**必需参数**

*name*

字符串，指定接触初始化存储库键。

**可选参数**

*overclosureType*

 SymbolicConstant，指定要定义的过闭合类型。可能的值为 ADJUST、INTERFERENCE 和 CLEARANCE。默认值为 ADJUST。

*interferenceDistance*

 `None` 或浮点数，指定干涉距离。此参数仅在 *overclosureType*=INTERFERENCE 时有效。默认值为 `None`。

*clearanceDistance*

 `None` 或浮点数，指定初始间隙距离。此参数仅在 *overclosureType*=CLEARANCE 时适用，且在那种情况下是必需的。默认值为 `None`。

*openingTolerance*

 `None` 或浮点数，指定初始开口将进行无应变调整的距离容差。此参数在 *overclosureType*=INTERFERENCE 时无效，除非为 *interferenceDistance* 指定了值。默认值为 `None`。

*overclosureTolerance*

 `None` 或浮点数，指定初始过闭合将进行无应变调整的距离容差。默认值为 `None`。

**返回值**

StdInitialization 对象。

**异常**

RangeError。

### 25.67.2 setValues(...)

此方法修改 StdInitialization 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [StdInitialization](pt01ch25pyo67.md#ker-stdinitialization-stdinitialization-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 25.67.3 成员

StdInitialization 对象的成员与 [StdInitialization](pt01ch25pyo67.md#ker-stdinitialization-stdinitialization-pyc) 方法的参数具有相同的名称和描述。

### 25.67.4 对应的分析关键字

| [*CONTACT INITIALIZATION DATA](../key/key-link.md#usb-kws-hcontactinitdata) |
| --- |



