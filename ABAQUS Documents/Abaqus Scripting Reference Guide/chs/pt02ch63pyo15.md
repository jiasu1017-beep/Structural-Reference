# 63.15 LayerProperties object







The LayerProperties object defines the properties of a layer of reinforcement for membrane, shell, and surface sections.

**Access**

```
sectionApi.sections()[*name*].rebarLayers().layerTable(*i*)
```

### 63.15.1 LayerProperties(...)

This method creates a LayerProperties object.

**Path**

```
LayerProperties
```

**Prototype**

```
odb_LayerProperties&
LayerProperties(double barArea,
                odb_Union orientationAngle,
                const odb_String& layerName,
                const odb_String& material,
                double barSpacing,
                double layerPosition,
                double spacingAngle,
                double extensionRatio,
                double radius);
```

**Required arguments**

*barArea*

A Double specifying the area per bar.

*orientationAngle*

An odb_Union specifying the orientation of the rebar. A Float specifies the angular orientation; a String specifies an orientation name.

*layerName*

An odb_String specifying the name of the rebar layer.

*material*

An odb_String specifying the name of the rebar material.

**Optional arguments**

*barSpacing*

A Double specifying the spacing of the rebar. This argument is only valid if the *rebarSpacing* argument on the parent [RebarLayers](pt02ch63pyo19.md) object is set to "CONSTANT". The default value is 0.0.

*layerPosition*

A Double specifying the position of the rebar from the middle surface of the shell. *layerPosition* applies only for homogeneous shell sections and composite shell sections. The default value is 0.0.

*spacingAngle*

A Double specifying the spacing angle of the rebar. This argument is only valid if the *rebarSpacing* argument on the parent [RebarLayers](pt02ch63pyo19.md) object is set to "ANGULAR". The default value is 0.0.

*extensionRatio*

A Double specifying the extension ratio for the rebar. This argument is only valid if the *rebarSpacing* argument on the parent [RebarLayers](pt02ch63pyo19.md) object is set to "LIFT_EQUATION". The default value is 0.0.

*radius*

A Double specifying the radius of the rebar. This argument is only valid if the *rebarSpacing* argument on the parent [RebarLayers](pt02ch63pyo19.md) object is set to "LIFT_EQUATION". The default value is 0.0.

**Return value**

A LayerProperties object.

**Exceptions**

None.

### 63.15.2 Members

The LayerProperties object has members with the same names and descriptions as the arguments to the [LayerProperties](pt02ch63pyo15.md#ker-layerproperties-layerproperties-cpp) method.

### 63.15.3 Corresponding analysis keywords

| [*REBAR LAYER](../key/key-link.md#usb-kws-mrebarlayer) |
| --- |




