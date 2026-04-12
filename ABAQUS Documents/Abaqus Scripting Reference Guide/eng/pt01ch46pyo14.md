# 46.14 HomogeneousSolidSection object







The HomogeneousSolidSection object defines the properties of a solid section.

The HomogeneousSolidSection object is derived from the [SolidSection](pt01ch46pyo22.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.14.1 HomogeneousSolidSection(...)

This method creates a HomogeneousSolidSection object.

**Path**

```
mdb.models[*name*].HomogeneousSolidSection
session.odbs[*name*].HomogeneousSolidSection
```

**Required arguments**

*name*

A String specifying the repository key.

*material*

A String specifying the name of the material.

**Optional argument**

*thickness*

 `None` or a Float specifying the thickness of the section. Possible values are None or a floating point value such that*thickness* ![](../graphics/ker_eqn00060.gif) 0.0. The default value is None.

**Return value**

A HomogeneousSolidSection object.

**Exceptions**

InvalidNameError and RangeError.

### 46.14.2 setValues(...)

This method modifies the HomogeneousSolidSection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [HomogeneousSolidSection](pt01ch46pyo14.md#ker-homogeneoussolidsection-homogeneoussolidsection-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 46.14.3 Members

The HomogeneousSolidSection object has members with the same names and descriptions as the arguments to the [HomogeneousSolidSection](pt01ch46pyo14.md#ker-homogeneoussolidsection-homogeneoussolidsection-pyc) method.

### 46.14.4 Corresponding analysis keywords

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |




