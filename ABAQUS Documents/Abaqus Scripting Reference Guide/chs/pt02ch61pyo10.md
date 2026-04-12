# 61.10 HistoryPoint 对象

HistoryPoint 对象指定收集历史数据的点。HistoryPoint 对象是一个临时对象，用作 `HistoryRegion` 方法的参数。

**访问**

```
odb.steps()[*name*].historyRegions()[*name*].point()
```

### 61.10.1 HistoryPoint(...)

此方法为节点创建 HistoryPoint 对象。

**路径**

```
HistoryPoint
```

**原型**

```
odb_HistoryPoint&
HistoryPoint(const odb_Node& node);
```

**必需参数**

*node*

一个 [OdbMeshNode](pt02ch61pyo19.md) 对象，指定要收集数据的节点。

**可选参数**

无。

**返回值**

一个 HistoryPoint 对象。

**异常**

无。

### 61.10.2 HistoryPoint(...)

此方法为元素创建 HistoryPoint 对象。

**路径**

```
odb.steps()[*name*].historyRegions()[*name*].HistoryPoint
```

**原型**

```
odb_HistoryPoint&
HistoryPoint(const odb_Element& element,
             int ipNumber,
             const odb_SectionPoint& sectionPoint,
             odb_Enum::odb_ElementFaceEnum face,
             const odb_Node& node);
```

**必需参数**

*element*

一个 [OdbMeshElement](pt02ch61pyo18.md) 对象，指定要收集数据的元素。

**可选参数**

*ipNumber*

一个 Int，指定积分点。此参数用于定义 odb_Enum::INTEGRATION_POINT 或 odb_Enum::ELEMENT_FACE_INTEGRATION_POINT 的历史输出位置。默认值为 0。

*sectionPoint*

一个 [SectionPoint](pt02ch61pyo28.md) 对象。

*face*

一个 odb_Enum::odb_ElementFaceEnum，指定元素面。此参数用于定义 odb_Enum::ELEMENT_FACE 或 odb_Enum::ELEMENT_FACE_INTEGRATION_POINT 的历史输出位置。可能的值为：
- odb_Enum::FACE_UNKOWN，指定此值表示未指定任何值。
- odb_Enum::FACE1，指定此值表示已指定元素面 1。
- odb_Enum::FACE2，指定此值表示已指定元素面 2。
- odb_Enum::FACE3，指定此值表示已指定元素面 3。
- odb_Enum::FACE4，指定此值表示已指定元素面 4。
- odb_Enum::FACE5，指定此值表示已指定元素面 5。
- odb_Enum::FACE6，指定此值表示已指定元素面 6。
- odb_Enum::SIDE1，指定此值表示已指定元素侧 1。
- odb_Enum::SIDE2，指定此值表示已指定元素侧 2。
- odb_Enum::END1，指定此值表示已指定元素端 1。
- odb_Enum::END2，指定此值表示已指定元素端 2。
- odb_Enum::END3，指定此值表示已指定元素端 3。

默认值为 odb_Enum::FACE_UNKNOWN。

*node*

一个 [OdbMeshNode](pt02ch61pyo19.md) 对象，指定要收集数据的节点。

**返回值**

一个 HistoryPoint 对象。

**异常**

无。

### 61.10.3 HistoryPoint(...)

此方法为区域创建 HistoryPoint 对象。

**路径**

```
odb.steps()[*name*].historyRegions()[*name*].HistoryPoint
```

**原型**

```
odb_HistoryPoint&
HistoryPoint(const odb_Set& region);
```

**必需参数**

*region*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定要收集数据的区域。

**可选参数**

无。

**返回值**

一个 HistoryPoint 对象。

**异常**

无。

### 61.10.4 HistoryPoint(...)

此方法为 [OdbAssembly](pt02ch61pyo13.md) 对象创建 HistoryPoint 对象。

**路径**

```
odb.steps()[*name*].historyRegions()[*name*].HistoryPoint
```

**原型**

```
odb_HistoryPoint&
HistoryPoint(const odb_Assembly& assembly);
```

**必需参数**

*assembly*

一个 [OdbAssembly](pt02ch61pyo13.md) 对象，指定要收集数据的装配。

**可选参数**

无。

**返回值**

一个 HistoryPoint 对象。

**异常**

无。

### 61.10.5 HistoryPoint(...)

此方法为 [OdbInstance](pt02ch61pyo16.md) 对象创建 HistoryPoint 对象。

**路径**

```
odb.steps()[*name*].historyRegions()[*name*].HistoryPoint
```

**原型**

```
odb_HistoryPoint&
HistoryPoint(const odb_Instance& instance);
```

**必需参数**

*instance*

一个 [OdbInstance](pt02ch61pyo16.md) 对象，指定要收集数据的实例。

**可选参数**

无。

**返回值**

一个 HistoryPoint 对象。

**异常**

无。

### 61.10.6 成员

HistoryPoint 对象具有与 [HistoryPoint](pt02ch61pyo10.md#ker-historypoint-historypoint-cpp) 方法参数相同名称和描述的成员。

此外，HistoryPoint 对象可以具有以下成员：

**原型**

```
odb_Node node() const;
odb_Element element() const;
int ipNumber() const;
odb_Enum::odb_ElementFaceEnum face() const;
odb_Enum::odb_ResultPositionEnum position() const;
odb_SectionPoint sectionPoint() const;
const odb_Set& region() const;
const odb_Instance& instance() const;
const odb_Assembly& assembly() const;
```

*ipNumber*

一个 Int，指定积分点。此参数用于定义 odb_Enum::INTEGRATION_POINT 或 odb_Enum::ELEMENT_FACE_INTEGRATION_POINT 的历史输出位置。默认值为 0。

*face*

一个 odb_Enum::odb_ElementFaceEnum，指定元素面。此参数用于定义 odb_Enum::ELEMENT_FACE 或 odb_Enum::ELEMENT_FACE_INTEGRATION_POINT 的历史输出位置。可能的值为：
- odb_Enum::FACE_UNKOWN，指定此值表示未指定任何值。
- odb_Enum::FACE1，指定此值表示已指定元素面 1。
- odb_Enum::FACE2，指定此值表示已指定元素面 2。
- odb_Enum::FACE3，指定此值表示已指定元素面 3。
- odb_Enum::FACE4，指定此值表示已指定元素面 4。
- odb_Enum::FACE5，指定此值表示已指定元素面 5。
- odb_Enum::FACE6，指定此值表示已指定元素面 6。
- odb_Enum::SIDE1，指定此值表示已指定元素侧 1。
- odb_Enum::SIDE2，指定此值表示已指定元素侧 2。
- odb_Enum::END1，指定此值表示已指定元素端 1。
- odb_Enum::END2，指定此值表示已指定元素端 2。
- odb_Enum::END3，指定此值表示已指定元素端 3。

默认值为 odb_Enum::FACE_UNKNOWN。

*position*

一个 odb_Enum::odb_ResultPositionEnum，指定历史点的结果位置。可能的值为：
- odb_Enum::NODAL，指定在节点处计算的值。
- odb_Enum::ELEMENT_NODAL，指定通过外推在积分点处计算的结果获得的值。
- odb_Enum::INTEGRATION_POINT，指定在积分点处计算的值。
- odb_Enum::ELEMENT_FACE，指定为诸如空腔辐射等针对元素表面面定义的面变量获得的结果。
- odb_Enum::ELEMENT_FACE_INTEGRATION_POINT，指定当表面面具有积分点时，为诸如空腔辐射等针对元素表面面定义的面变量获得的结果。
- odb_Enum::WHOLE_ELEMENT，指定为整个元素变量获得的结果。
- odb_Enum::WHOLE_REGION，指定整个模型区域的结果。
- odb_Enum::WHOLE_PART_INSTANCE，指定整个部件实例的结果。
- odb_Enum::WHOLE_MODEL，指定整个模型的结果。

*element*

一个 [OdbMeshElement](pt02ch61pyo18.md) 对象，指定要收集数据的元素。

*sectionPoint*

一个 [SectionPoint](pt02ch61pyo28.md) 对象。

*region*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定要收集数据的区域。

*assembly*

一个 [OdbAssembly](pt02ch61pyo13.md) 对象，指定要收集数据的装配。

*instance*

一个 [OdbInstance](pt02ch61pyo16.md) 对象，指定要收集数据的实例。
