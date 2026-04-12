# 46.9 EulerianSection object







The EulerianSection object defines the properties of a Eulerian section.

The EulerianSection object is derived from the [Section](pt01ch46pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.9.1 EulerianSection(...)

This method creates a EulerianSection object.

**Path**

```
mdb.models[*name*].EulerianSection
session.odbs[*name*].EulerianSection
```

**Required arguments**

*name*

A String specifying the repository key.

*data*

A String-to-String Dictionary specifying a dictionary mapping Material instance names to Material names. Internally the specified mapping gets sorted on Material instance name.

**Optional arguments**

None.

**Return value**

An EulerianSection object.

**Exceptions**

None.

### 46.9.2 setValues(...)

This method modifies the EulerianSection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [EulerianSection](pt01ch46pyo09.md#ker-euleriansection-euleriansection-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 46.9.3 Members

The EulerianSection object has members with the same names and descriptions as the arguments to the [EulerianSection](pt01ch46pyo09.md#ker-euleriansection-euleriansection-pyc) method.

### 46.9.4 Corresponding analysis keywords

| [*EULERIAN SECTION](../key/key-link.md#usb-kws-meulsection) |
| --- |




