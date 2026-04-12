# 19.16 XFEMCrack 对象









XFEMCrack 对象定义使用 XFEM 技术建模裂缝萌生或裂缝扩展所需的参数。当前仅支持装配区域。

XFEMCrack 对象派生自 [Crack](pt01ch19pyo04.md) 对象。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.cracks[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.cracks[*name*]
```

### 19.16.1 XFEMCrack(...)

此方法创建 XFEMCrack 对象。尽管构造函数可用于部件和装配，但 XFEMCrack 对象目前仅在装配下支持。

**路径**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.XFEMCrack
mdb.models[*name*].rootAssembly.engineeringFeatures.XFEMCrack
```

**必需参数**

*name*

一个 String，指定存储库键。

*crackDomain*

一个 [Region](pt01ch45pyo03.md) 对象，指定包含裂缝或可能包含裂缝的区域。

**可选参数**

*allowCrackGrowth*

一个 Boolean，指定是否允许裂缝扩展（增长）。默认值为 ON。

*crackLocation*

一个 [Region](pt01ch45pyo03.md) 对象，指定初始裂缝位置。当 *allowCrackGrowth*=OFF 时需要此参数。

*singularityCalcRadius*

`None` 或一个 Float，指定用于裂缝奇异性计算的从裂缝尖端开始的半径，在此半径内的元素用于裂缝奇异性计算。此参数仅在 *allowCrackGrowth*=OFF 时适用。默认值为 `None`。

*interactionProperty*

一个 String，指定定义裂缝表面接触属性的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。默认值为空字符串。

*elemId*

一个 Int 序列，指定与初始裂缝位置相交的元素的标签。此参数仅由输入文件读取器使用。

*nodeId*

一个 Int 序列，指定相应元素连接中节点的位置。此参数仅由输入文件读取器使用。

*hasCrackFront*

一个 Int 序列，指定指示 *crackFrontDist* 值包含/排除的值。零值表示未为第 i 对 *elemId* 和 *nodeId* 指定 *crackFrontDist*。此参数仅由输入文件读取器使用。

*crackPlaneDist*

一个 Float 序列，指定第一个有符号距离函数的值。此参数由输入文件读取器使用。

*crackFrontDist*

一个 Float 序列，指定第二个有符号距离函数的值。此参数仅由输入文件读取器使用。

**返回值**

一个 XFEMCrack 对象。

**异常**

无。

### 19.16.2 setValues(...)

此方法修改 XFEMCrack 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [XFEMCrack](pt01ch19pyo16.md#ker-xfemcrack-xfemcrack-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 19.16.3 成员

XFEMCrack 对象具有与 [XFEMCrack](pt01ch19pyo16.md#ker-xfemcrack-xfemcrack-pyc) 方法的参数相同的名称和描述的成员。

此外，XFEMCrack 对象还有以下成员：

*suppressed*

一个 Boolean，指定裂缝是否被抑制。默认值为 OFF。

### 19.16.4 对应的分析关键字

| [*ENRICHMENT](../key/key-link.md#usb-kws-menrichment) |
| --- |

| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=ENRICHMENT |
| --- |





