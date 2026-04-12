# 46.3 AcousticInterfaceSection object







The AcousticInterfaceSection object defines the properties of an acoustic section.

The AcousticInterfaceSection object is derived from the [Section](pt01ch46pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.3.1 AcousticInterfaceSection(...)

This method creates an AcousticInterfaceSection object.

**Path**

```
mdb.models[*name*].AcousticInterfaceSection
session.odbs[*name*].AcousticInterfaceSection
```

**Required argument**

*name*

A String specifying the repository key.

**Optional argument**

*thickness*

A Float specifying the thickness of the section. Possible values are *thickness* ![](../graphics/ker_eqn00060.gif) 0.0. The default value is 1.0.

**Return value**

An AcousticInterfaceSection object.

**Exceptions**

InvalidNameError and RangeError.

### 46.3.2 setValues(...)

This method modifies the AcousticInterfaceSection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [AcousticInterfaceSection](pt01ch46pyo03.md#ker-acousticinterfacesection-acousticinterfacesection-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 46.3.3 Members

The AcousticInterfaceSection object has members with the same names and descriptions as the arguments to the [AcousticInterfaceSection](pt01ch46pyo03.md#ker-acousticinterfacesection-acousticinterfacesection-pyc) method.

### 46.3.4 Corresponding analysis keywords

| [*INTERFACE](../key/key-link.md#usb-kws-minterface) |
| --- |




