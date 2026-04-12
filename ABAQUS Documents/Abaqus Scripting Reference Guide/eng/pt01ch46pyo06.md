# 46.6 CompositeShellSection object







The CompositeShellSection object defines the properties of a composite shell section.

The CompositeShellSection object is derived from the [GeometryShellSection](pt01ch46pyo12.md) object.

**Access**

```
import section
mdb.models[*name*].parts[*name*].compositeLayups[*i*].section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.6.1 CompositeShellSection(...)

This method creates a CompositeShellSection object.

**Path**

```
mdb.models[*name*].parts[*name*].compositeLayups[*i*].CompositeShellSection
mdb.models[*name*].CompositeShellSection
session.odbs[*name*].CompositeShellSection
```

**Required arguments**

*name*

A String specifying the repository key.

*layup*

A [SectionLayerArray](pt01ch46pyo20.md) object specifying the shell cross-section.

**Optional arguments**

*symmetric*

A Boolean specifying whether or not the layup should be made symmetric by the analysis. The default value is OFF.

*thicknessType*

A SymbolicConstant specifying the distribution used for defining the thickness of the elements. Possible values are UNIFORM, ANALYTICAL_FIELD, DISCRETE_FIELD, NODAL_ANALYTICAL_FIELD, and NODAL_DISCRETE_FIELD. The default value is UNIFORM.

*preIntegrate*

A Boolean specifying whether the shell section properties are specified by the user prior to the analysis (ON) or integrated during the analysis (OFF). The default value is OFF.

*poissonDefinition*

A SymbolicConstant specifying whether to use the default value for the Poisson's ratio. Possible values are:
- DEFAULT, specifying that the default value for the Poisson's ratio is 0.5 in an Abaqus/Standard analysis and is obtained from the material definition in an Abaqus/Explicit analysis.
- VALUE, specifying that the Poisson's ratio used in the analysis is the value provided in *poisson*.

The default value is DEFAULT.

*poisson*

A Float specifying the Poisson's ratio. Possible values are 1.0 ![](../graphics/ker_eqn00013.gif) *poisson* ![](../graphics/ker_eqn00013.gif) 0.5. This argument is valid only when *poissonDefinition*=VALUE. The default value is 0.5.

*integrationRule*

A SymbolicConstant specifying the shell section integration rule. Possible values are SIMPSON and GAUSS. The default value is SIMPSON.

*temperature*

A SymbolicConstant specifying the mode used for temperature and field variable input across the section thickness. Possible values are GRADIENT and POINTWISE. The default value is GRADIENT.

*idealization*

A SymbolicConstant specifying the mechanical idealization used for the section calculations. This member is only                            applicable when *preIntegrate* is set to ON. Possible values are NO_IDEALIZATION, SMEAR_ALL_LAYERS, MEMBRANE, and BENDING. The default value is NO_IDEALIZATION.

*nTemp*

 `None` or an Int specifying the number of temperature points to be input. This argument is valid only when *temperature*=POINTWISE. The default value is `None`.

*thicknessModulus*

 `None` or a Float specifying the effective thickness modulus. This argument is relevant only for continuum shells and must be used in conjunction with the argument *poisson*. The default value is `None`.

*useDensity*

A Boolean specifying whether or not to use the value of *density*. The default value is OFF.

*density*

A Float specifying the value of density to apply to this section. The default value is 0.0.

*layupName*

A String specifying the layup name for this section. The default value is an empty string.

*thicknessField*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object used to define the thickness of the shell elements. The *thicknessField* argument applies only when *thicknessType*=ANALYTICAL_FIELD or *thicknessType*=DISCRETE_FIELD. The default value is an empty string.

*nodalThicknessField*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object used to define the thickness of the shell elements at each node. The *nodalThicknessField* argument applies only when *thicknessType*=NODAL_ANALYTICAL_FIELD or *thicknessType*=NODAL_DISCRETE_FIELD. The default value is an empty string.

**Return value**

A CompositeShellSection object.

**Exceptions**

None.

### 46.6.2 setValues(...)

This method modifies the CompositeShellSection object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CompositeShellSection](pt01ch46pyo06.md#ker-compositeshellsection-compositeshellsection-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 46.6.3 Members

The CompositeShellSection object has members with the same names and descriptions as the arguments to the [CompositeShellSection](pt01ch46pyo06.md#ker-compositeshellsection-compositeshellsection-pyc) method.

In addition, the CompositeShellSection object can have the following members:

*rebarLayers*

A [RebarLayers](pt01ch46pyo19.md) object specifying reinforcement properties.

*transverseShear*

A [TransverseShearShell](pt01ch46pyo25.md) object specifying the transverse shear stiffness properties.

### 46.6.4 Corresponding analysis keywords

| [*SHELL SECTION](../key/key-link.md#usb-kws-mshellsection) |
| --- |
| [*SHELL GENERAL SECTION](../key/key-link.md#usb-kws-mshellgensect) |




