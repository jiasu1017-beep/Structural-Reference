# 25.30 ExpContactControl 对象

ExpContactControl 对象在 Abaqus/Explicit 分析中用于指定涉及物体之间接触的问题的可选解控制。

ExpContactControl 对象派生自 [ContactControl](pt01ch25pyo16.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].contactControls[*name*]
```

### 25.30.1 ExpContactControl(...)

此方法创建一个 ExpContactControl 对象。

**路径**

```
mdb.models[*name*].ExpContactControl
```

**必需参数**

*name*

字符串，指定接触控制存储库键。

**可选参数**

*globTrkChoice*

 SymbolicConstant，指定是否为全局接触搜索之间的最大增量数使用默认值。可能的值为 DEFAULT 和 SPECIFY。默认值为 DEFAULT。

*globTrkInc*

整数，指定全局接触搜索之间的最大增量数。*globTrkInc* 参数仅在 *globTrkChoice*=SPECIFY 时适用。对于表面到表面接触，默认值为 100；对于自接触，默认值为 4。

*fastLocalTrk*

布尔值，指定是否使用计算效率更高的局部跟踪方法。默认值为 ON。

*scalePenalty*

浮点数，指定 Abaqus/Explicit 缩放默认惩罚刚度的因子，以获得用于惩罚接触对的刚度。默认值为 1.0。

*warpCheckPeriod*

整数，指定检查主表面上高度翘曲面元的增量数。默认值为 20。

*warpCutoff*

浮点数，指定面元被认为高度翘曲的平面外翘曲角（度）。默认值为 20.0。

**返回值**

ExpContactControl 对象。

**异常**

RangeError。

### 25.30.2 setValues(...)

此方法修改 ExpContactControl 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ExpContactControl](pt01ch25pyo30.md#ker-expcontactcontrol-expcontactcontrol-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

RangeError。

### 25.30.3 成员

ExpContactControl 对象的成员与 [ExpContactControl](pt01ch25pyo30.md#ker-expcontactcontrol-expcontactcontrol-pyc) 方法的参数具有相同的名称和描述。

### 25.30.4 对应的分析关键字

| [*CONTACT CONTROLS](../key/key-link.md#usb-kws-hcontactcontrols) |
| --- |



