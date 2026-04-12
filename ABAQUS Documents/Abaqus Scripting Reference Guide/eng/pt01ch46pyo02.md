# 46.2 AcousticInfiniteSection object







The AcousticInfiniteSection object defines the properties of an acoustic section.

The AcousticInfiniteSection object is derived from the [Section](pt01ch46pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.2.1 AcousticInfiniteSection(...)

This method creates an AcousticInfiniteSection object.

**Path**

```
mdb.models[*name*].AcousticInfiniteSection
session.odbs[*name*].AcousticInfiniteSection
```

**Required arguments**

*name*

A String specifying the repository key.

*material*

A String specifying the name of the material.

**Optional arguments**

*thickness*

A Float specifying the thickness of the section. Possible values are *thickness* ![](../graphics/ker_eqn00060.gif) 0.0. The default value is 1.0.

*order*

An Int specifying the number of ninth-order polynomials that will be used to resolve the variation of the acoustic field in the infinite direction. Possible values are 0 ![](../graphics/ker_eqn00048.gif) *order* ![](../graphics/ker_eqn00013.gif) 10. The default value is 10.

**Return value**

An AcousticInfiniteSection object.

**Exceptions**

InvalidNameError and RangeError.

### 46.2.2 setValues(...)

This method modifies the AcousticInfiniteSection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [AcousticInfiniteSection](pt01ch46pyo02.md#ker-acousticinfinitesection-acousticinfinitesection-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 46.2.3 Members

The AcousticInfiniteSection object has members with the same names and descriptions as the arguments to the [AcousticInfiniteSection](pt01ch46pyo02.md#ker-acousticinfinitesection-acousticinfinitesection-pyc) method.

### 46.2.4 Corresponding analysis keywords

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |




