# 34.16 OdbLoadCase object







The OdbLoadCase object describes a load case.

**Access**

```
import odbAccess
session.odbs[*name*].steps[*name*].frames[*i*].loadCase
session.odbs[*name*].steps[*name*].historyRegions[*name*].loadCase
session.odbs[*name*].steps[*name*].loadCases[*name*]
```

### 34.16.1 LoadCase(...)

This method creates an OdbLoadCase object.

**Path**

```
session.odbs[*name*].steps[*name*].LoadCase
```

**Required argument**

*name*

A String specifying the name of the OdbLoadCase object.

**Optional arguments**

None.

**Return value**

An OdbLoadCase object.

**Exceptions**

None.

### 34.16.2 Members

The OdbLoadCase object has members with the same names and descriptions as the arguments to the [LoadCase](pt01ch34pyo16.md#ker-odbloadcase-loadcase-pyc) method.




