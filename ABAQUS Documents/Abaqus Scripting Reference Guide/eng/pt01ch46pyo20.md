# 46.20 SectionLayer object







The SectionLayer object defines the material layer in a composite shell.

**Access**

```
import section
mdb.models[*name*].parts[*name*].compositeLayups[*i*].section.layup[*i*]
mdb.models[*name*].sections[*name*].layup[*i*]
import odbSection
session.odbs[*name*].sections[*name*].layup[*i*]
```

### 46.20.1 SectionLayer(...)

This method creates a SectionLayer object.

**Path**

```
section.SectionLayer
```

```
odbSection.SectionLayer
```

**Required arguments**

*thickness*

A Float specifying the thickness of the section layer.

*material*

A String specifying the name of the section layer material.

**Optional arguments**

*orientAngle*

A Float or a String specifying the relative orientation of the section layer. A Float specifies the angular orientation; a String specifies a user-subroutine orientation name. If a String is specified, a user-subroutine orientation is used, otherwise the Float value is used as an angular orientation. The default value is 0.0.

*numIntPts*

An Int specifying the number of integration points to be used through the section. This argument is valid only if the *preIntegrate* argument on the parent [CompositeShellSection](pt01ch46pyo06.md) object is set to ON. The default value is 3.

*axis*

A SymbolicConstant specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation is applied. For shells this axis is also the shell normal. This only applies if a valid reference is provided for the orientation. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_3.

*angle*

A Float specifying the angle of the additional rotation. This only applies if a valid reference is provided for the orientation. The default value is 0.0.

*additionalRotationType*

A SymbolicConstant specifying the method used to describe the additional rotation when a valid orientation is specified. Possible values are ROTATION_NONE, ROTATION_ANGLE, and ROTATION_FIELD. The default value is ROTATION_NONE.

*thicknessType*

A SymbolicConstant specifying the method used to describe the thickness. Possible values are THICKNESS_MAGNITUDE and THICKNESS_DISCRETE_FIELD. The default value is THICKNESS_MAGNITUDE.

*plyName*

A String specifying the ply identifier for this section layer. The default value is "".

*orientation*

The SymbolicConstant None or a [DatumCsys](pt01ch15pyo03.md) object specifying a coordinate system reference for the relative orientation of this layer. If this reference is valid it is used as the relative orientation of the layer, otherwise the *orientAngle* is used as described.  The default value is None.

*additionalRotationField*

A String specifying the name of the field specifying the additional rotation. The default value is "".

*thicknessField*

A String specifying the name of the field specifying the thickness The default value is "".

**Return value**

A SectionLayer object.

**Exceptions**

None.

### 46.20.2 Members

The SectionLayer object has members with the same names and descriptions as the arguments to the [SectionLayer](pt01ch46pyo20.md#ker-sectionlayer-sectionlayer-pyc) method.

### 46.20.3 Corresponding analysis keywords

| [*SHELL SECTION](../key/key-link.md#usb-kws-mshellsection) |
| --- |
| [*SHELL GENERAL SECTION](../key/key-link.md#usb-kws-mshellgensect) |




