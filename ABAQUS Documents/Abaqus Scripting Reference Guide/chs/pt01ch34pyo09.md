# 34.9 HistoryPoint 对象

HistoryPoint 对象指定要收集历史数据的点。HistoryPoint 对象是一个临时对象，用作 `HistoryRegion` 方法的参数。

**访问**

```
import odbAccess
session.odbs[*name*].steps[*name*].historyRegions[*name*].point
```

### 34.9.1 HistoryPoint(...)

此方法为节点创建 HistoryPoint 对象。

**路径**

```
odbAccess.HistoryPoint
```

**必要参数**

*node*

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象，指定要收集数据的节点。

**可选参数**

无。

**返回值**

HistoryPoint 对象。

**异常**

无。

### 34.9.2 HistoryPoint(...)

此方法为单元创建 HistoryPoint 对象。

**路径**

```
session.odbs[*name*].steps[*name*].historyRegions[*name*].HistoryPoint
```

**必要参数**

*element*

一个 [OdbMeshElement](pt01ch34pyo17.md) 对象，指定要收集数据的单元。

**可选参数**

*ipNumber*

一个整数，指定积分点。此参数用于定义 INTEGRATION_POINT 或 ELEMENT_FACE_INTEGRATION_POINT 的历史输出位置。默认值为 0。

*sectionPoint*

一个 [SectionPoint](pt01ch34pyo28.md) 对象。

*face*

一个 SymbolicConstant，指定元素面。此参数用于定义 ELEMENT_FACE 或 ELEMENT_FACE_INTEGRATION_POINT 的历史输出位置。可能的值为：
- FACE_UNKOWN，指定此值表示未指定任何值。
- FACE1，指定此值表示已指定元素面 1。
- FACE2，指定此值表示已指定元素面 2。
- FACE3，指定此值表示已指定元素面 3。
- FACE4，指定此值表示已指定元素面 4。
- FACE5，指定此值表示已指定元素面 5。
- FACE6，指定此值表示已指定元素面 6。
- SIDE1，指定此值表示已指定元素侧面 1。
- SIDE2，指定此值表示已指定元素侧面 2。
- END1，指定此值表示已指定元素端 1。
- END2，指定此值表示已指定元素端 2。
- END3，指定此值表示已指定元素端 3。

默认值为 FACE_UNKNOWN。

*node*

一个 [OdbMeshNode](pt01ch34pyo18.md) 对象，指定要收集数据的节点。

**返回值**

HistoryPoint 对象。

**异常**

无。

### 34.9.3 HistoryPoint(...)

此方法为区域创建 HistoryPoint 对象。

**路径**

```
session.odbs[*name*].steps[*name*].historyRegions[*name*].HistoryPoint
```

**必要参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定要收集数据的区域。

**可选参数**

无。

**返回值**

HistoryPoint 对象。

**异常**

无。

### 34.9.4 HistoryPoint(...)

此方法为 [OdbAssembly](pt01ch34pyo12.md) 对象创建 HistoryPoint 对象。

**路径**

```
session.odbs[*name*].steps[*name*].historyRegions[*name*].HistoryPoint
```

**必要参数**

*assembly*

一个 [OdbAssembly](pt01ch34pyo12.md) 对象，指定要收集数据的装配。

**可选参数**

无。

**返回值**

HistoryPoint 对象。

**异常**

无。

### 34.9.5 HistoryPoint(...)

此方法为 [OdbInstance](pt01ch34pyo15.md) 对象创建 HistoryPoint 对象。

**路径**

```
session.odbs[*name*].steps[*name*].historyRegions[*name*].HistoryPoint
```

**必要参数**

*instance*

一个 [OdbInstance](pt01ch34pyo15.md) 对象，指定要收集数据的实例。

**可选参数**

无。

**返回值**

HistoryPoint 对象。

**异常**

无。

### 34.9.6 成员

HistoryPoint 对象具有与 [HistoryPoint](pt01ch34pyo09.md#ker-historypoint-historypoint-pyc) 方法的参数名称和描述相同的成员。

此外，HistoryPoint 对象可以具有以下成员：

*ipNumber*

一个整数，指定积分点。此参数用于定义 INTEGRATION_POINT 或 ELEMENT_FACE_INTEGRATION_POINT 的历史输出位置。默认值为 0。

*face*

一个 SymbolicConstant，指定元素面。此参数用于定义 ELEMENT_FACE 或 ELEMENT_FACE_INTEGRATION_POINT 的历史输出位置。可能的值为：
- FACE_UNKOWN，指定此值表示未指定任何值。
- FACE1，指定此值表示已指定元素面 1。
- FACE2，指定此值表示已指定元素面 2。
- FACE3，指定此值表示已指定元素面 3。
- FACE4，指定此值表示已指定元素面 4。
- FACE5，指定此值表示已指定元素面 5。
- FACE6，指定此值表示已指定元素面 6。
- SIDE1，指定此值表示已指定元素侧面 1。
- SIDE2，指定此值表示已指定元素侧面 2。
- END1，指定此值表示已指定元素端 1。
- END2，指定此值表示已指定元素端 2。
- END3，指定此值表示已指定元素端 3。

默认值为 FACE_UNKNOWN。

*position*

一个 SymbolicConstant，指定历史点的结果位置。可能的值为：
- NODAL，指定在节点处计算的值。
- ELEMENT_NODAL，指定通过外推在积分点处计算的结果获得的值。
- INTEGRATION_POINT，指定在积分点处计算的值。
- ELEMENT_FACE，指定为元素表面定义的表面变量（如空腔辐射）的结果。
- ELEMENT_FACE_INTEGRATION_POINT，指定为表面变量（如空腔辐射）获得的结果，这些结果在为表面面定义了积分点的元素表面处定义。
- WHOLE_ELEMENT，指定为整个单元变量获得的结果。
- WHOLE_REGION，指定整个模型区域的结果。
- WHOLE_PART_INSTANCE，指定模型整个部件实例的结果。
- WHOLE_MODEL，指定整个模型的结果。

*element*

一个 [OdbMeshElement](pt01ch34pyo17.md) 对象，指定要收集数据的单元。

*sectionPoint*

一个 [SectionPoint](pt01ch34pyo28.md) 对象。

*region*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定要收集数据的区域。

*assembly*

一个 [OdbAssembly](pt01ch34pyo12.md) 对象，指定要收集数据的装配。

*instance*

一个 [OdbInstance](pt01ch34pyo15.md) 对象，指定要收集数据的实例。
