# 46.5 CohesiveSection object







The CohesiveSection object defines the properties of a cohesive section.

The CohesiveSection object is derived from the [Section](pt01ch46pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.5.1 CohesiveSection(...)

This method creates a CohesiveSection object.

**Path**

```
mdb.models[*name*].CohesiveSection
session.odbs[*name*].CohesiveSection
```

**Required arguments**

*name*

A String specifying the repository key.

*response*

A SymbolicConstant specifying the geometric assumption that defines the constitutive behavior of the cohesive elements. Possible values are TRACTION_SEPARATION, CONTINUUM, and GASKET.

*material*

A String specifying the name of the material.

**Optional arguments**

*initialThicknessType*

A SymbolicConstant specifying the method used to compute the initial thickness. Possible values are:
- SOLVER_DEFAULT, specifying that Abaqus will use the analysis product default
- GEOMETRY, specifying that Abaqus will compute the thickness from the nodal coordinates of the elements.
- SPECIFY, specifying that Abaqus will use the value given for *initialThickness*

The default value is SOLVER_DEFAULT.

*initialThickness*

A Float specifying the initial thickness for the section. The *initialThickness* argument applies only when *initialThicknessType*=SPECIFY. The default value is 1.0.

*outOfPlaneThickness*

 `None` or a Float specifying the out-of-plane thickness for the section. The default value is `None`.

**Return value**

A CohesiveSection object.

**Exceptions**

RangeError and InvalidNameError.

### 46.5.2 setValues(...)

This method modifies the CohesiveSection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CohesiveSection](pt01ch46pyo05.md#ker-cohesivesection-cohesivesection-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 46.5.3 Members

The CohesiveSection object has members with the same names and descriptions as the arguments to the [CohesiveSection](pt01ch46pyo05.md#ker-cohesivesection-cohesivesection-pyc) method.

### 46.5.4 Corresponding analysis keywords

| [*COHESIVE SECTION](../key/key-link.md#usb-kws-mcohesivesection) |
| --- |




