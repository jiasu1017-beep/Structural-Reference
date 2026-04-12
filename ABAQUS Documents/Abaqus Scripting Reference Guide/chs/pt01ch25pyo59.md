# 25.59 RegionPairs 对象

RegionPairs 对象存储 [ContactExp](pt01ch25pyo19.md) 和 [ContactStd](pt01ch25pyo24.md) 对象的域对定义。RegionPairs 对象没有构造函数或成员。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*].excludedPairs
mdb.models[*name*].interactions[*name*].includedPairs
```

### 25.59.1 setValuesInStep(...)

此方法允许在给定步骤中添加和移除域对。

**必需参数**

*stepName*

String，指定要修改域对分配的步骤名称。

**可选参数**

*useAllstar*

布尔值，指定接触面对是否由模型中的所有外露面组成，在 Abaqus/Explicit 分析中还包括解析刚性表面、壳边缘和梁段。

*addPairs*

区域对象或 SymbolicConstant 对序列，指定要添加到给定步骤中 [ContactExp](pt01ch25pyo19.md) 或 [ContactStd](pt01ch25pyo24.md) 对象包含对中的表面对。SymbolicConstant 的可能值为 GLOBAL 和 SELF。当与 [ContactExp](pt01ch25pyo19.md) 对象一起使用时，每对中的第二个参数也可以是引用欧拉材料表面的字符串。

*removePairs*

区域对象或 SymbolicConstant 对序列，指定要从给定步骤中 [ContactExp](pt01ch25pyo19.md) 或 [ContactStd](pt01ch25pyo24.md) 对象的包含对中移除的表面对。SymbolicConstant 的可能值为 GLOBAL 和 SELF。当与 [ContactExp](pt01ch25pyo19.md) 对象一起使用时，每对中的第二个参数也可以是引用欧拉材料表面的字符串。

**返回值**

无。

**异常**

无。

### 25.59.2 成员

RegionPairs 对象没有成员。

### 25.59.3 对应的分析关键字

| [*CONTACT INCLUSIONS](../key/key-link.md#usb-kws-hcontactinclusions) |
| --- |
| [*CONTACT EXCLUSIONS](../key/key-link.md#usb-kws-hcontactexclusions) |
