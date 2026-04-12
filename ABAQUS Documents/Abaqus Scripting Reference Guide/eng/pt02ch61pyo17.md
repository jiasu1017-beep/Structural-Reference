# 61.17 OdbLoadCase object







The OdbLoadCase object describes a load case.

**Access**

```
odb.steps()[*name*].frames(*i*).loadCase()
odb.steps()[*name*].historyRegions()[*name*].loadCase()
odb.steps()[*name*].loadCases()[*name*]
```

### 61.17.1 LoadCase(...)

This method creates an OdbLoadCase object.

**Path**

```
odb.steps()[*name*].LoadCase
```

**Prototype**

```
odb_LoadCase&
LoadCase(const odb_String& name);
```

**Required argument**

*name*

An odb_String specifying the name of the OdbLoadCase object.

**Optional arguments**

None.

**Return value**

An OdbLoadCase object.

**Exceptions**

None.

### 61.17.2 Members

The OdbLoadCase object has members with the same names and descriptions as the arguments to the [LoadCase](pt02ch61pyo17.md#ker-odbloadcase-loadcase-cpp) method.




