# 46.16 MembraneSection object







The MembraneSection object defines the properties of a membrane section.

The MembraneSection object is derived from the [Section](pt01ch46pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.16.1 MembraneSection(...)

This method creates a MembraneSection object.

**Path**

```
mdb.models[*name*].MembraneSection
session.odbs[*name*].MembraneSection
```

**Required arguments**

*name*

A String specifying the repository key.

*material*

A String specifying the name of the material.

**Optional arguments**

*thickness*

A Float specifying the thickness for the section. Possible values are *thickness* ![](../graphics/ker_eqn00060.gif) 0.0. The default value is 1.0.

*thicknessType*

A SymbolicConstant specifying the distribution used for defining the thickness of the elements. Possible values are UNIFORM, ANALYTICAL_FIELD, and DISCRETE_FIELD. The default value is UNIFORM.

*poissonDefinition*

A SymbolicConstant specifying whether to use the default value for the Poisson's ratio. Possible values are:
- DEFAULT, specifying that the default value for the Poisson's ratio is 0.5 in an Abaqus/Standard analysis and is obtained from the material definition in an Abaqus/Explicit analysis.
- VALUE, specifying that the Poisson's ratio used in the analysis is the value provided in *poisson*.

The default value is DEFAULT.

*poisson*

A Float specifying the section Poisson's ratio. Possible values are 1.0 ![](../graphics/ker_eqn00013.gif) *poisson* ![](../graphics/ker_eqn00013.gif) 0.5. This argument is valid only when *poissonDefinition*=VALUE. The default value is 0.5.

*thicknessField*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object used to define the thickness of the shell elements. The *thicknessField* argument applies only when *thicknessType*=ANALYTICAL_FIELD or *thicknessType*=DISCRETE_FIELD. The default value is an empty string.

**Return value**

A MembraneSection object.

**Exceptions**

RangeError and InvalidNameError.

### 46.16.2 setValues(...)

This method modifies the MembraneSection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [MembraneSection](pt01ch46pyo16.md#ker-membranesection-membranesection-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

RangeError.

### 46.16.3 Members

The MembraneSection object has members with the same names and descriptions as the arguments to the [MembraneSection](pt01ch46pyo16.md#ker-membranesection-membranesection-pyc) method.

In addition, the MembraneSection object can have the following member:

*rebarLayers*

A [RebarLayers](pt01ch46pyo19.md) object specifying reinforcement properties.

### 46.16.4 Corresponding analysis keywords

| [*MEMBRANE SECTION](../key/key-link.md#usb-kws-mmembranesection) |
| --- |




