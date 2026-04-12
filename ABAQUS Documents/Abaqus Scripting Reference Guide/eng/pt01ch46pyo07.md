# 46.7 CompositeSolidSection object







The CompositeSolidSection object defines the properties of a composite solid section.

The CompositeSolidSection object is derived from the [Section](pt01ch46pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.7.1 CompositeSolidSection(...)

This method creates a CompositeSolidSection object.

**Path**

```
mdb.models[*name*].CompositeSolidSection
session.odbs[*name*].CompositeSolidSection
```

**Required arguments**

*name*

A String specifying the repository key.

*layup*

A [SectionLayerArray](pt01ch46pyo20.md) object specifying the solid cross-section.

**Optional arguments**

*symmetric*

A Boolean specifying whether or not the layup should be made symmetric by the analysis. The default value is OFF.

*layupName*

A String specifying the layup name for this section. The default value is an empty string.

**Return value**

A CompositeSolidSection object.

**Exceptions**

None.

### 46.7.2 setValues(...)

This method modifies the CompositeSolidSection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CompositeSolidSection](pt01ch46pyo07.md#ker-compositesolidsection-compositesolidsection-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 46.7.3 Members

The CompositeSolidSection object has members with the same names and descriptions as the arguments to the [CompositeSolidSection](pt01ch46pyo07.md#ker-compositesolidsection-compositesolidsection-pyc) method.

### 46.7.4 Corresponding analysis keywords

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |




