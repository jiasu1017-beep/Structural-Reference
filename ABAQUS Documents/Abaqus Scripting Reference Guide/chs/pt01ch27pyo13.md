# 27.13 BoltLoad 对象





BoltLoad 对象定义螺栓载荷。

BoltLoad 对象派生自 [Load](pt01ch27pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.13.1 BoltLoad(...)

此方法创建 BoltLoad 对象。

**路径**

```
mdb.models[*name*].BoltLoad
```

**必需参数**

*name*

一个 String，指定载荷存储库密钥。

*createStepName*

一个 String，指定创建载荷的步骤名称。这必须是第一个分析步骤名称。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用载荷的区域。

*magnitude*

一个 Float，指定螺栓载荷大小。

*datumAxis*

一个 [DatumAxis](pt01ch15pyo02.md) 对象，指定预紧截面的法向方向。

**注意：***datumAxis* 仅对实体和壳体区域必需；对线缆区域无意义。

**可选参数**

*boltMethod*

一个 SymbolicConstant，指定施加螺栓载荷的方法。可能的值为 APPLY_FORCE 和 ADJUST_LENGTH。默认值为 APPLY_FORCE。

*amplitude*

一个 String 或 SymbolicConstant UNSET，指定幅值参考的名称。如果载荷没有幅值参考，应使用 UNSET。默认值为 UNSET。只有当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

一个 BoltLoad 对象。

**异常**

TextError。

### 27.13.2 setValues(...)

此方法修改创建载荷的步骤中现有 BoltLoad 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BoltLoad](pt01ch27pyo13.md#ker-boltload-boltload-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无

**异常**

无。

### 27.13.3 setValuesInStep(...)

此方法修改指定步骤中现有 BoltLoad 对象的传播数据。

**必需参数**

*stepName*

一个 String，指定修改载荷的步骤名称。

**可选参数**

*boltMethod*

一个 SymbolicConstant，指定螺栓载荷的类型。可能的值为 APPLY_FORCE、ADJUST_LENGTH 和 FIX_LENGTH。默认值为 APPLY_FORCE。

*magnitude*

一个 Float，指定螺栓载荷大小。

*amplitude*

一个 String 或 SymbolicConstant，指定幅值参考的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果要从上一个分析步骤传播幅值，应使用 UNCHANGED。如果要将载荷更改为没有幅值参考，应使用 FREED。只有当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

无

**异常**

无。

### 27.13.4 成员

BoltLoad 对象可以具有以下成员：

*name*

一个 String，指定载荷存储库密钥。

*datumAxis*

一个 [DatumAxis](pt01ch15pyo02.md) 对象，指定预紧截面的法向方向。

**注意：***datumAxis* 仅对实体和壳体区域必需；对线缆区域无意义。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用载荷的区域。

### 27.13.5 对应的分析关键字

| [*PRE-TENSION SECTION](../key/key-link.md#usb-kws-mpretension) |
| --- |
| [*NODE](../key/key-link.md#usb-kws-mnode) (用于参考节点) |
| [*NSET](../key/key-link.md#usb-kws-mnset) (用于参考节点) |




