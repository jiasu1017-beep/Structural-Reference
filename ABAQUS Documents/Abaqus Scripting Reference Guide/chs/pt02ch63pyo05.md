# 63.5 CohesiveSection object







The CohesiveSection object defines the properties of a cohesive section.

The CohesiveSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.5.1 CohesiveSection(...)

This method creates a CohesiveSection object.

**Path**

```
sectionApi.CohesiveSection
```

**Prototype**

```
odb_CohesiveSection&
CohesiveSection(const odb_String& name,
                const odb_String& response,
                const odb_String& material,
                const odb_String& initialThicknessType,
                double initialThickness,
                odb_Union outOfPlaneThickness);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*response*

An odb_String specifying the geometric assumption that defines the constitutive behavior of the cohesive elements. Possible values are "TRACTION_SEPARATION", "CONTINUUM", and "GASKET".

*material*

An odb_String specifying the name of the material.

**Optional arguments**

*initialThicknessType*

An odb_String specifying the method used to compute the initial thickness. Possible values are:
- "SOLVER_DEFAULT", specifying that Abaqus will use the analysis product default
- "GEOMETRY", specifying that Abaqus will compute the thickness from the nodal coordinates of the elements.
- "SPECIFY", specifying that Abaqus will use the value given for *initialThickness*

The default value is "SOLVER_DEFAULT".

*initialThickness*

A Double specifying the initial thickness for the section. The *initialThickness* argument applies only when *initialThicknessType*="SPECIFY". The default value is 1.0.

*outOfPlaneThickness*

The string "NONE" or a Double specifying the out-of-plane thickness for the section. The default value is "NONE".

**Return value**

A CohesiveSection object.

**Exceptions**

RangeError and InvalidNameError.

### 63.5.2 Members

The CohesiveSection object has members with the same names and descriptions as the arguments to the [CohesiveSection](pt02ch63pyo05.md#ker-cohesivesection-cohesivesection-cpp) method.

### 63.5.3 Corresponding analysis keywords

| [*COHESIVE SECTION](../key/key-link.md#usb-kws-mcohesivesection) |
| --- |




