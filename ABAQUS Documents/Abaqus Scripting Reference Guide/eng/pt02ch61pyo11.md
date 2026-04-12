# 61.11 HistoryRegion object







The HistoryRegion object contains history data for a single location in the model.

**Access**

```
odb.steps()[*name*].historyRegions()[*name*]
```

### 61.11.1 HistoryRegion(...)

This method creates a HistoryRegion object.

**Path**

```
odb.steps()[*name*].HistoryRegion
```

**Prototype**

```
odb_HistoryRegion&
HistoryRegion(const odb_String& name,
              const odb_String& description,
              const odb_HistoryPoint& point,
              const odb_LoadCase& loadCase);
```

**Required arguments**

*name*

An odb_String specifying the name of the HistoryRegion object.

*description*

An odb_String specifying the description of the HistoryRegion object.

*point*

A [HistoryPoint](pt02ch61pyo10.md) object specifying the point to which the history data refer.

**Optional argument**

*loadCase*

An [OdbLoadCase](pt02ch61pyo17.md) object specifying the load case associated with the HistoryRegion object.

**Return value**

A HistoryRegion object.

**Exceptions**

None.

### 61.11.2 getSubset(...)

This method returns a subset of the data in the HistoryRegion object.

**Prototype**

```
odb_HistoryRegion
getSubset(const odb_String& variableName);
```

**Required argument**

*variableName*

A String specifying the name of the output variable to return.

**Optional arguments**

None.

**Return value**

A HistoryRegion object.

**Exceptions**

None.

### 61.11.3 getSubset(...)

This method returns a subset of the data in the HistoryRegion object.

**Prototype**

```
odb_HistoryRegion
getSubset(float start);
```

**Required argument**

*start*

A Float specifying the start of the subset. This is the same as the first item in the data array member of the [HistoryOutput](pt02ch61pyo09.md) object.

**Optional arguments**

None.

**Return value**

A HistoryRegion object.

**Exceptions**

None.

### 61.11.4 getSubset(...)

This method returns a subset of the data in the HistoryRegion object.

**Prototype**

```
odb_HistoryRegion
getSubset(float start,
          float end);
```

**Required arguments**

*start*

A Float specifying the start of the subset. This is the same as the first item in the data array member of the [HistoryOutput](pt02ch61pyo09.md) object.

*end*

A Float specifying the end of the subset.

**Optional arguments**

None.

**Return value**

A HistoryRegion object.

**Exceptions**

None.

### 61.11.5 Members

The HistoryRegion object has members with the same names and descriptions as the arguments to the [HistoryRegion](pt02ch61pyo11.md#ker-historyregion-historyregion-cpp) method.

In addition, the HistoryRegion object can have the following members:

**Prototype**

```
odb_String description() const;
const odb_LoadCase& loadCase() const;
odb_String name() const;
odb_HistoryPoint point() const;
odb_Enum::odb_ResultPositionEnum position() const;
const odb_HistoryOutputRepository& historyOutputs();
```

*position*

An odb_Enum::odb_ResultPositionEnum specifying the position of the history output. Possible values are odb_Enum::NODAL, odb_Enum::INTEGRATION_POINT, odb_Enum::WHOLE_ELEMENT, odb_Enum::WHOLE_REGION, and odb_Enum::WHOLE_MODEL.

*historyOutputs*

A repository of [HistoryOutput](pt02ch61pyo09.md) objects.




