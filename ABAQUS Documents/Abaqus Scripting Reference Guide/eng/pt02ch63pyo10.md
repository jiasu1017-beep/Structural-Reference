# 63.10 GasketSection object







The GasketSection object defines the properties of a gasket section.

The GasketSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.10.1 GasketSection(...)

This method creates a GasketSection object.

**Path**

```
sectionApi.GasketSection
```

**Prototype**

```
odb_GasketSection&
GasketSection(const odb_String& name,
              const odb_String& material,
              double crossSection,
              double initialGap,
              odb_Union initialThickness,
              double initialVoid,
              odb_Union stabilizationStiffness);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*material*

An odb_String specifying the name of the material of which the gasket is made or material that defines gasket behavior.

**Optional arguments**

*crossSection*

A Double specifying the cross-sectional area, width, or out-of-plane thickness, if applicable, depending on the gasket element type. The default value is 1.0.

*initialGap*

A Double specifying the initial gap. The default value is 0.0.

*initialThickness*

The string "DEFAULT" or a Double specifying the initial gasket thickness. If "DEFAULT" is specified, the initial thickness is determined using nodal coordinates. The default value is "DEFAULT".

*initialVoid*

A Double specifying the initial void. The default value is 0.0.

*stabilizationStiffness*

The string "DEFAULT" or a Double specifying the default stabilization stiffness used in all but link elements to stabilize gasket elements that are not supported at all nodes, such as those that extend outside neighboring components. If "DEFAULT" is specified, a value is used equal to 10–9 times the initial compressive stiffness in the thickness direction. The default value is "DEFAULT".

**Return value**

A GasketSection object.

**Exceptions**

InvalidNameError and ValueError.

### 63.10.2 Members

The GasketSection object has members with the same names and descriptions as the arguments to the [GasketSection](pt02ch63pyo10.md#ker-gasketsection-gasketsection-cpp) method.

### 63.10.3 Corresponding analysis keywords

| [*GASKET SECTION](../key/key-link.md#usb-kws-mgasketsection) |
| --- |




