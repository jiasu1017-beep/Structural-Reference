# 46.24 TransverseShearBeam object







The TransverseShearBeam object defines the transverse shear stiffness properties of a beam section.

**Access**

```
import section
mdb.models[*name*].sections[*name*].beamTransverseShear
import odbSection
session.odbs[*name*].sections[*name*].beamTransverseShear
```

### 46.24.1 TransverseShearBeam(...)

This method creates a TransverseShearBeam object.

**Path**

```
mdb.models[*name*].sections[*name*].TransverseShearBeam
session.odbs[*name*].sections[*name*].TransverseShearBeam
```

**Required argument**

*scfDefinition*

A SymbolicConstant specifying how slenderness compensation factor of the section is given. Possible values are ANALYSIS_DEFAULT, COMPUTED, and VALUE.

**Optional arguments**

*k23*

 `None` or a Float specifying the k23 shear stiffness of the section. The default value is `None`.

*k13*

 `None` or a Float specifying the k13 shear stiffness of the section. The default value is `None`.

*slendernessCompensation*

The SymbolicConstant COMPUTED or a Float specifying the slenderness compensation factor of the section. The default value is 0.25.

**Return value**

A TransverseShearBeam object.

**Exceptions**

None.

### 46.24.2 setValues(...)

This method modifies the TransverseShearBeam object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TransverseShearBeam](pt01ch46pyo24.md#ker-transverseshearbeam-transverseshearbeam-pyc) method.

**Return value**

None

**Exceptions**

None.

### 46.24.3 Members

The TransverseShearBeam object has members with the same names and descriptions as the arguments to the [TransverseShearBeam](pt01ch46pyo24.md#ker-transverseshearbeam-transverseshearbeam-pyc) method.

### 46.24.4 Corresponding analysis keywords

| [*TRANSVERSE SHEAR STIFFNESS](../key/key-link.md#usb-kws-mtransshearstiff) |
| --- |




