# 63.13 HomogeneousShellSection object







The HomogeneousShellSection object defines the properties of a shell section.

The HomogeneousShellSection object is derived from the [GeometryShellSection](pt02ch63pyo12.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.13.1 HomogeneousShellSection(...)

This method creates a HomogeneousShellSection object.

**Path**

```
sectionApi.HomogeneousShellSection
```

**Prototype**

```
odb_HomogeneousShellSection& 
         HomogeneousShellSection(const odb_String& name,
           double thickness,
           const odb_String& material,
           int numIntPts,
           odb_String thicknessType,
           bool preIntegrate,
           odb_String poissonDefinition,
           double poisson,
           odb_String integrationRule,
           odb_String temperature,
           odb_String simplification,
           odb_Union nTemp,
           odb_Union thicknessModulus,
           bool useDensity,
           double density,
           odb_String thicknessField,
           odb_String nodalThicknessField);

```

**Required arguments**

*name*

An odb_String specifying the repository key.

*thickness*

                  A Double specifying the thickness of the section. The *thickness* argument applies only when *thicknessType*="UNIFORM".                

*material*

An odb_String specifying the name of the section material.

**Optional arguments**

*numIntPts*

An Int specifying the number of integration points to be used through the section. Possible values are *numIntPts* ![](../graphics/ker_eqn00060.gif) 0. The default value is 5.

To use the default settings of the analysis products, set *numIntPts* to 5 if *integrationRule*="SIMPSON" or set *numIntPts* to 7 if *integrationRule*="GAUSS".

*thicknessType*

An odb_String specifying the distribution used for defining the thickness of the elements. Possible values are "UNIFORM", "ANALYTICAL_FIELD", "DISCRETE_FIELD", "NODAL_ANALYTICAL_FIELD", and "NODAL_DISCRETE_FIELD". The default value is "UNIFORM".

*preIntegrate*

A Boolean specifying whether the shell section properties are specified by the user prior to the analysis (true) or integrated during the analysis (false). The default value is false.

*poissonDefinition*

An odb_String specifying whether to use the default value for the Poisson's ratio. Possible values are:
- "DEFAULT", specifying that the default value for the Poisson's ratio is 0.5 in an Abaqus/Standard analysis and is obtained from the material definition in an Abaqus/Explicit analysis.
- "VALUE", specifying that the Poisson's ratio used in the analysis is the value provided in *poisson*.

The default value is "DEFAULT".

*poisson*

A Double specifying the Poisson's ratio. Possible values are 1.0 ![](../graphics/ker_eqn00013.gif) *poisson* ![](../graphics/ker_eqn00013.gif) 0.5. This argument is valid only when *poissonDefinition*="VALUE". The default value is 0.5.

*integrationRule*

An odb_String specifying the shell section integration rule. Possible values are "SIMPSON" and "GAUSS". The default value is "SIMPSON".

*temperature*

An odb_String specifying the mode used for temperature and field variable input across the section thickness. Possible values are "GRADIENT" and "POINTWISE". The default value is "GRADIENT".

*idealization*

An odb_String specifying the mechanical idealization used for the section calculations. This member is only                            applicable when *preIntegrate* is set to true. Possible values are "NO_IDEALIZATION", "SMEAR_ALL_LAYERS", "MEMBRANE", and "BENDING". The default value is "NO_IDEALIZATION".

*nTemp*

The string "NONE" or an Int specifying the number of temperature points to be input. This argument is valid only when *temperature*="POINTWISE". The default value is "NONE".

*thicknessModulus*

The string "NONE" or a Double specifying the effective thickness modulus. This argument is relevant only for continuum shells and must be used in conjunction with the argument *poisson*. The default value is "NONE".

*useDensity*

A Boolean specifying whether or not to use the value of *density*. The default value is false.

*density*

A Double specifying the value of density to apply to this section. The default value is 0.0.

*thicknessField*

An odb_String specifying the name of the [AnalyticalField](#ker-analyticalfield-cpp) or [DiscreteField](#ker-discretefield-cpp) object used to define the thickness of the shell elements. The *thicknessField* argument applies only when *thicknessType*="ANALYTICAL_FIELD" or *thicknessType*="DISCRETE_FIELD". The default value is an empty string.

*nodalThicknessField*

An odb_String specifying the name of the [AnalyticalField](#ker-analyticalfield-cpp) or [DiscreteField](#ker-discretefield-cpp) object used to define the thickness of the shell elements at each node. The *nodalThicknessField* argument applies only when *thicknessType*="NODAL_ANALYTICAL_FIELD" or *thicknessType*="NODAL_DISCRETE_FIELD". The default value is an empty string.

**Return value**

A HomogeneousShellSection object.

**Exceptions**

None.

### 63.13.2 Members

The HomogeneousShellSection object has members with the same names and descriptions as the arguments to the [HomogeneousShellSection](pt02ch63pyo13.md#ker-homogeneousshellsection-homogeneousshellsection-cpp) method.

In addition, the HomogeneousShellSection object can have the following members:

**Prototype**

```
odb_RebarLayers rebarLayers() const;
odb_TransverseShearShell transverseShear() const;
```

*rebarLayers*

A [RebarLayers](pt02ch63pyo19.md) object specifying reinforcement properties.

*transverseShear*

A [TransverseShearShell](pt02ch63pyo25.md) object specifying the transverse shear stiffness properties.

### 63.13.3 Corresponding analysis keywords

| [*SHELL SECTION](../key/key-link.md#usb-kws-mshellsection) |
| --- |
| [*SHELL GENERAL SECTION](../key/key-link.md#usb-kws-mshellgensect) |




