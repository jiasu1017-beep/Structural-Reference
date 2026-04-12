# 63.16 MembraneSection object







The MembraneSection object defines the properties of a membrane section.

The MembraneSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.16.1 MembraneSection(...)

This method creates a MembraneSection object.

**Path**

```
sectionApi.MembraneSection
```

**Prototype**

```
odb_MembraneSection&
MembraneSection(const odb_String& name,
                const odb_String& material,
                double thickness,
                const odb_String& thicknessType,
                const odb_String& poissonDefinition,
                double poisson,
                const odb_String& thicknessField);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*material*

An odb_String specifying the name of the material.

**Optional arguments**

*thickness*

A Double specifying the thickness for the section. Possible values are *thickness* ![](../graphics/ker_eqn00060.gif) 0.0. The default value is 1.0.

*thicknessType*

An odb_String specifying the distribution used for defining the thickness of the elements. Possible values are "UNIFORM", "ANALYTICAL_FIELD", and "DISCRETE_FIELD". The default value is "UNIFORM".

*poissonDefinition*

An odb_String specifying whether to use the default value for the Poisson's ratio. Possible values are:
- "DEFAULT", specifying that the default value for the Poisson's ratio is 0.5 in an Abaqus/Standard analysis and is obtained from the material definition in an Abaqus/Explicit analysis.
- "VALUE", specifying that the Poisson's ratio used in the analysis is the value provided in *poisson*.

The default value is "DEFAULT".

*poisson*

A Double specifying the section Poisson's ratio. Possible values are 1.0 ![](../graphics/ker_eqn00013.gif) *poisson* ![](../graphics/ker_eqn00013.gif) 0.5. This argument is valid only when *poissonDefinition*="VALUE". The default value is 0.5.

*thicknessField*

An odb_String specifying the name of the [AnalyticalField](#ker-analyticalfield-cpp) or [DiscreteField](#ker-discretefield-cpp) object used to define the thickness of the shell elements. The *thicknessField* argument applies only when *thicknessType*="ANALYTICAL_FIELD" or *thicknessType*="DISCRETE_FIELD". The default value is an empty string.

**Return value**

A MembraneSection object.

**Exceptions**

RangeError and InvalidNameError.

### 63.16.2 Members

The MembraneSection object has members with the same names and descriptions as the arguments to the [MembraneSection](pt02ch63pyo16.md#ker-membranesection-membranesection-cpp) method.

In addition, the MembraneSection object can have the following member:

**Prototype**

```
odb_RebarLayers rebarLayers() const;
```

*rebarLayers*

A [RebarLayers](pt02ch63pyo19.md) object specifying reinforcement properties.

### 63.16.3 Corresponding analysis keywords

| [*MEMBRANE SECTION](../key/key-link.md#usb-kws-mmembranesection) |
| --- |




