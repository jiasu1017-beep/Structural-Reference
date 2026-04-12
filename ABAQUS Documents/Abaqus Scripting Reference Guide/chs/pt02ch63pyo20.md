# 63.20 SectionLayer object







The SectionLayer object defines the material layer in a composite shell.

**Access**

```
sectionApi.sections()[*name*].layup(*i*)
```

### 63.20.1 SectionLayer(...)

This method creates a SectionLayer object.

**Path**

```
SectionLayer
```

**Prototype**

```
odb_SectionLayer&
SectionLayer(double thickness,
             const odb_String& material,
             odb_Union orientAngle,
             int numIntPts,
             const odb_String& axis,
             float angle,
             const odb_String& additionalRotationType,
             const odb_String& thicknessType,
             const odb_String& plyName,
             const odb_DatumCsys& orientation,
             const odb_String& additionalRotationField,
             const odb_String& thicknessField);
```

**Required arguments**

*thickness*

A Double specifying the thickness of the section layer.

*material*

An odb_String specifying the name of the section layer material.

**Optional arguments**

*orientAngle*

An odb_Union specifying the relative orientation of the section layer. A Float specifies the angular orientation; a String specifies a user-subroutine orientation name. If a String is specified, a user-subroutine orientation is used, otherwise the Float value is used as an angular orientation. The default value is 0.0.

*numIntPts*

An Int specifying the number of integration points to be used through the section. This argument is valid only if the *preIntegrate* argument on the parent [CompositeShellSection](pt02ch63pyo06.md) object is set to true. The default value is 3.

*axis*

An odb_String specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation is applied. For shells this axis is also the shell normal. This only applies if a valid reference is provided for the orientation. Possible values are "AXIS_1", "AXIS_2", and "AXIS_3". The default value is "AXIS_3".

*angle*

A Float specifying the angle of the additional rotation. This only applies if a valid reference is provided for the orientation. The default value is 0.0.

*additionalRotationType*

An odb_String specifying the method used to describe the additional rotation when a valid orientation is specified. Possible values are "ROTATION_NONE", "ROTATION_ANGLE", and "ROTATION_FIELD". The default value is "ROTATION_NONE".

*thicknessType*

An odb_String specifying the method used to describe the thickness. Possible values are "THICKNESS_MAGNITUDE" and "THICKNESS_DISCRETE_FIELD". The default value is "THICKNESS_MAGNITUDE".

*plyName*

An odb_String specifying the ply identifier for this section layer. The default value is "".

*orientation*

A [DatumCsys](#ker-datumcsys-cpp) object specifying a coordinate system reference for the relative orientation of this layer. If this reference is valid it is used as the relative orientation of the layer, otherwise the *orientAngle* is used as described. 

*additionalRotationField*

An odb_String specifying the name of the field specifying the additional rotation. The default value is "".

*thicknessField*

An odb_String specifying the name of the field specifying the thickness The default value is "".

**Return value**

A SectionLayer object.

**Exceptions**

None.

### 63.20.2 Members

The SectionLayer object has members with the same names and descriptions as the arguments to the [SectionLayer](pt02ch63pyo20.md#ker-sectionlayer-sectionlayer-cpp) method.

### 63.20.3 Corresponding analysis keywords

| [*SHELL SECTION](../key/key-link.md#usb-kws-mshellsection) |
| --- |
| [*SHELL GENERAL SECTION](../key/key-link.md#usb-kws-mshellgensect) |




