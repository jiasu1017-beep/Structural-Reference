# 46.18 PEGSection object







The PEGSection object defines the properties of a solid section.

The PEGSection object is derived from the [Section](pt01ch46pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.18.1 PEGSection(...)

This method creates a PEGSection object.

**Path**

```
mdb.models[*name*].PEGSection
session.odbs[*name*].PEGSection
```

**Required arguments**

*name*

A String specifying the repository key.

*material*

A String specifying the name of the material.

**Optional arguments**

*thickness*

A Float specifying the thickness of the section. Possible values are *thickness* ![](../graphics/ker_eqn00060.gif) 0.0. The default value is 1.0.

*wedgeAngle1*

A Float specifying the value of the x component of the angle between the bounding planes, ![](../graphics/ker_eqn00415.gif). The default value is 0.0.

*wedgeAngle2*

A Float specifying the value of the y component of the angle between the bounding planes, ![](../graphics/ker_eqn00416.gif). The default value is 0.0.

**Return value**

A PEGSection object.

**Exceptions**

InvalidNameError and RangeError.

### 46.18.2 setValues(...)

This method modifies the PEGSection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PEGSection](pt01ch46pyo18.md#ker-pegsection-pegsection-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 46.18.3 Members

The PEGSection object has members with the same names and descriptions as the arguments to the [PEGSection](pt01ch46pyo18.md#ker-pegsection-pegsection-pyc) method.

### 46.18.4 Corresponding analysis keywords

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |




