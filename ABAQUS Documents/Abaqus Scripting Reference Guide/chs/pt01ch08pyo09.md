# 8.9 PipeProfile 对象

PipeProfile 对象定义圆形管 profile 的属性。

PipeProfile 对象派生自 [Profile](pt01ch08pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].profiles[*name*]
import odbSection
session.odbs[*name*].profiles[*name*]
```

### 8.9.1 PipeProfile(...)

此方法创建一个 PipeProfile 对象。

**路径**

```
mdb.models[*name*].PipeProfile
session.odbs[*name*].PipeProfile
```

**必需参数**

*name*

一个 String，指定存储库键。

*r*

一个 Float，指定管的外半径。有关详细信息，请参阅《Abaqus Analysis User's Guide》的"Beam cross-section library," Section 29.3.9。

*t*

一个 Float，指定管的壁厚。

**可选参数**

*formulation*

一个 SymbolicConstant，指定公式。可能的值为 THIN_WALL 和 THICK_WALL。默认值为 THIN_WALL。

**返回值**

一个 PipeProfile 对象。

**异常**

RangeError。

### 8.9.2 setValues(...)

此方法修改 PipeProfile 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [PipeProfile](pt01ch08pyo09.md#ker-pipeprofile-pipeprofile-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 8.9.3 成员

PipeProfile 对象具有与 [PipeProfile](pt01ch08pyo09.md#ker-pipeprofile-pipeprofile-pyc) 方法参数具有相同名称和描述的成员。

### 8.9.4 对应的分析关键字

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=PIPE |
| --- |

| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection), SECTION=THICK PIPE |
| --- |
