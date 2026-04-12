# 61.10 HistoryPoint object







The HistoryPoint object specifies the point at which history data will be collected. The HistoryPoint object is a temporary object used as an argument to the `HistoryRegion` method.

**Access**

```
odb.steps()[*name*].historyRegions()[*name*].point()
```

### 61.10.1 HistoryPoint(...)

This method creates a HistoryPoint object for a node.

**Path**

```
HistoryPoint
```

**Prototype**

```
odb_HistoryPoint&
HistoryPoint(const odb_Node& node);
```

**Required argument**

*node*

An [OdbMeshNode](pt02ch61pyo19.md) object specifying the node for which the data are to be collected.

**Optional arguments**

None.

**Return value**

A HistoryPoint object.

**Exceptions**

None.

### 61.10.2 HistoryPoint(...)

This method creates a HistoryPoint object for an element.

**Path**

```
odb.steps()[*name*].historyRegions()[*name*].HistoryPoint
```

**Prototype**

```
odb_HistoryPoint&
HistoryPoint(const odb_Element& element,
             int ipNumber,
             const odb_SectionPoint& sectionPoint,
             odb_Enum::odb_ElementFaceEnum face,
             const odb_Node& node);
```

**Required argument**

*element*

An [OdbMeshElement](pt02ch61pyo18.md) object specifying the element for which the data are to be collected.

**Optional arguments**

*ipNumber*

An Int specifying the integration point.  This argument is used to define a history output position of odb_Enum::INTEGRATION_POINT or odb_Enum::ELEMENT_FACE_INTEGRATION_POINT. The default value is 0.

*sectionPoint*

A [SectionPoint](pt02ch61pyo28.md) object.

*face*

An odb_Enum::odb_ElementFaceEnum specifying the element face.  This argument is used to define a history output position of odb_Enum::ELEMENT_FACE or odb_Enum::ELEMENT_FACE_INTEGRATION_POINT. Possible values are:
- odb_Enum::FACE_UNKOWN, specifying this value indicates that no value has been specified.
- odb_Enum::FACE1, specifying this value indicates that element face 1 has been specified.
- odb_Enum::FACE2, specifying this value indicates that element face 2 has been specified.
- odb_Enum::FACE3, specifying this value indicates that element face 3 has been specified.
- odb_Enum::FACE4, specifying this value indicates that element face 4 has been specified.
- odb_Enum::FACE5, specifying this value indicates that element face 5 has been specified.
- odb_Enum::FACE6, specifying this value indicates that element face 6 has been specified.
- odb_Enum::SIDE1, specifying this value indicates that element side 1 has been specified.
- odb_Enum::SIDE2, specifying this value indicates element side 2 has been specified.
- odb_Enum::END1, specifying this value indicates that element end 1 has been specified.
- odb_Enum::END2, specifying this value indicates that element end 2 has been specified.
- odb_Enum::END3, specifying this value indicates that element end 3 has been specified.

The default value is odb_Enum::FACE_UNKNOWN.

*node*

An [OdbMeshNode](pt02ch61pyo19.md) object specifying the node for which the data are to be collected.

**Return value**

A HistoryPoint object.

**Exceptions**

None.

### 61.10.3 HistoryPoint(...)

This method creates a HistoryPoint object for a region.

**Path**

```
odb.steps()[*name*].historyRegions()[*name*].HistoryPoint
```

**Prototype**

```
odb_HistoryPoint&
HistoryPoint(const odb_Set& region);
```

**Required argument**

*region*

An [OdbSet](pt02ch61pyo24.md) object specifying the region for which the data are to be collected.

**Optional arguments**

None.

**Return value**

A HistoryPoint object.

**Exceptions**

None.

### 61.10.4 HistoryPoint(...)

This method creates a HistoryPoint object for the [OdbAssembly](pt02ch61pyo13.md) object.

**Path**

```
odb.steps()[*name*].historyRegions()[*name*].HistoryPoint
```

**Prototype**

```
odb_HistoryPoint&
HistoryPoint(const odb_Assembly& assembly);
```

**Required argument**

*assembly*

An [OdbAssembly](pt02ch61pyo13.md) object specifying the assembly for which the data are to be collected.

**Optional arguments**

None.

**Return value**

A HistoryPoint object.

**Exceptions**

None.

### 61.10.5 HistoryPoint(...)

This method creates a HistoryPoint object for the [OdbInstance](pt02ch61pyo16.md) object.

**Path**

```
odb.steps()[*name*].historyRegions()[*name*].HistoryPoint
```

**Prototype**

```
odb_HistoryPoint&
HistoryPoint(const odb_Instance& instance);
```

**Required argument**

*instance*

An [OdbInstance](pt02ch61pyo16.md) object specifying the instance for which the data are to be collected.

**Optional arguments**

None.

**Return value**

A HistoryPoint object.

**Exceptions**

None.

### 61.10.6 Members

The HistoryPoint object has members with the same names and descriptions as the arguments to the [HistoryPoint](pt02ch61pyo10.md#ker-historypoint-historypoint-cpp) method.

In addition, the HistoryPoint object can have the following members:

**Prototype**

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

An Int specifying the integration point.  This argument is used to define a history output position of odb_Enum::INTEGRATION_POINT or odb_Enum::ELEMENT_FACE_INTEGRATION_POINT. The default value is 0.

*face*

An odb_Enum::odb_ElementFaceEnum specifying the element face.  This argument is used to define a history output position of odb_Enum::ELEMENT_FACE or odb_Enum::ELEMENT_FACE_INTEGRATION_POINT. Possible values are:
- odb_Enum::FACE_UNKOWN, specifying this value indicates that no value has been specified.
- odb_Enum::FACE1, specifying this value indicates that element face 1 has been specified.
- odb_Enum::FACE2, specifying this value indicates that element face 2 has been specified.
- odb_Enum::FACE3, specifying this value indicates that element face 3 has been specified.
- odb_Enum::FACE4, specifying this value indicates that element face 4 has been specified.
- odb_Enum::FACE5, specifying this value indicates that element face 5 has been specified.
- odb_Enum::FACE6, specifying this value indicates that element face 6 has been specified.
- odb_Enum::SIDE1, specifying this value indicates that element side 1 has been specified.
- odb_Enum::SIDE2, specifying this value indicates element side 2 has been specified.
- odb_Enum::END1, specifying this value indicates that element end 1 has been specified.
- odb_Enum::END2, specifying this value indicates that element end 2 has been specified.
- odb_Enum::END3, specifying this value indicates that element end 3 has been specified.

The default value is odb_Enum::FACE_UNKNOWN.

*position*

An odb_Enum::odb_ResultPositionEnum specifying the result position of the history point. Possible values are:
- odb_Enum::NODAL, specifying the values calculated at the nodes.
- odb_Enum::ELEMENT_NODAL, specifying the values obtained by extrapolating results calculated at the integration points.
- odb_Enum::INTEGRATION_POINT, specifying the values calculated at the integration points.
- odb_Enum::ELEMENT_FACE, specifying the results obtained for surface variables such as cavity radiation that are defined for the surface facets of an element.
- odb_Enum::ELEMENT_FACE_INTEGRATION_POINT, specifying the results obtained for surface variables such as cavity radiation that are defined for the surface facets of an element when the surface facets have integration points.
- odb_Enum::WHOLE_ELEMENT, specifying the results obtained for whole element variables.
- odb_Enum::WHOLE_REGION, specifying the results for an entire region of the model.
- odb_Enum::WHOLE_PART_INSTANCE, specifying the results for an entire part instance of the model.
- odb_Enum::WHOLE_MODEL, specifying the results for the entire model.

*element*

An [OdbMeshElement](pt02ch61pyo18.md) object specifying the element for which the data are to be collected.

*sectionPoint*

A [SectionPoint](pt02ch61pyo28.md) object.

*region*

An [OdbSet](pt02ch61pyo24.md) object specifying the region for which the data are to be collected.

*assembly*

An [OdbAssembly](pt02ch61pyo13.md) object specifying the assembly for which the data are to be collected.

*instance*

An [OdbInstance](pt02ch61pyo16.md) object specifying the instance for which the data are to be collected.




