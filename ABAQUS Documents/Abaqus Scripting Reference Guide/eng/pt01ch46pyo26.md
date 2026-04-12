# 46.26 TrussSection object







The TrussSection object defines the properties of a truss section.

The TrussSection object is derived from the [Section](pt01ch46pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.26.1 TrussSection(...)

This method creates a TrussSection object.

**Path**

```
mdb.models[*name*].TrussSection
session.odbs[*name*].TrussSection
```

**Required arguments**

*name*

A String specifying the repository key.

*material*

A String specifying the name of the material.

**Optional argument**

*area*

A Float specifying the cross-sectional area for the section. Possible values are *area* ![](../graphics/ker_eqn00060.gif) 0. The default value is 1.0.

**Return value**

A TrussSection object.

**Exceptions**

RangeError and InvalidNameError.

### 46.26.2 setValues(...)

This method modifies the TrussSection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TrussSection](pt01ch46pyo26.md#ker-trusssection-trusssection-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 46.26.3 Members

The TrussSection object has members with the same names and descriptions as the arguments to the [TrussSection](pt01ch46pyo26.md#ker-trusssection-trusssection-pyc) method.

### 46.26.4 Corresponding analysis keywords

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |




