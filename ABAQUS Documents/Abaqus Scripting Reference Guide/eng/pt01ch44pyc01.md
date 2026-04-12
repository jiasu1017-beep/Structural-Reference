# 44.6 Property assignment commands







The Property assignment commands are used to assign and unassign properties to parts. The `part` and `section` modules must be imported to give access to the Property assignment commands.

**Access**

```
import part
import section
```

### 44.6.1 assignBeamSectionOrientation(...)

This method assigns a beam section orientation to a region of a part.

**Path**

```
mdb.models[*name*].parts[*name*].assignBeamSectionOrientation
```

**Required arguments**

*region*

A sequence of geomSequences of Edge objects or a sequence of sequences of one-dimensional elements.

*method*

A SymbolicConstant specifying the assignment method. Only a value of N1_COSINES is currently supported.

*n1*

A sequence of three Floats specifying the approximate local ![](../graphics/ker_eqn00406.gif)-direction of the beam cross-section.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 44.6.2 assignMaterialOrientation(...)

This method assigns a material orientation to a region.

**Path**

```
mdb.models[*name*].parts[*name*].assignMaterialOrientation
```

**Required argument**

*region*

A sequence of geomSequences of Vertex, Edge, Face, and Cell objects or a sequence of sequences of elements.

*localCsys*

A Datum object specifying the local coordinate system or `None`, indicating the global coordinate system. 

**Optional arguments**

*axis*

A SymbolicConstant specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation is applied. For shells this axis is also the shell normal. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.

*angle*

A Float specifying the angle of the additional rotation. The default value is 0.0.

**Return value**

None

**Exceptions**

None.

### 44.6.3 assignRebarOrientation(...)

This method assigns a rebar reference orientation to a region.

**Path**

```
mdb.models[*name*].parts[*name*].assignRebarOrientation
```

**Required argument**

*region*

A sequence of geomSequences of Vertex, Edge, Face, and Cell objects or a sequence of sequences of elements.

*localCsys*

A Datum object specifying the local coordinate system or `None`, indicating the global coordinate system. 

**Optional arguments**

*axis*

A SymbolicConstant specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation is applied. For shells this axis is also the shell normal. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.

*angle*

A Float specifying the angle of the additional rotation. The default value is 0.0.

**Return value**

None

**Exceptions**

None.

### 44.6.4 flipNormal(...)

This method flips the normals of shell or membrane elements of an orphan mesh or of two-dimensional geometric regions.

**Path**

```
mdb.models[*name*].parts[*name*].flipNormal
```

**Required argument**

*regions*

A Region object specifying the region on which normals are flipped. For 3D parts, the region contains Face objects or two-dimensional triangle or quadrilateral Element objects. For axisymmetric parts, the region contains Edge objects or line Elements objects.

**Optional argument**

*referenceRegion*

A two-dimensional element object whose normal is to be matched. If unspecified, all the normals associated with the given regions will be flipped. The *referenceRegion* argument is applicable only if the argument regions contain a sequence of quadrilateral or triangular elements.

**Return value**

None

**Exceptions**

None.

### 44.6.5 flipTangent(...)

This method flips the tangents of beam or truss elements of an orphan mesh or of one-dimensional geometric regions.

**Path**

```
mdb.models[*name*].parts[*name*].flipTangent
```

**Required argument**

*regions*

A Region object specifying the region on which normals are flipped. The region contains Edge objects or one-dimensional Element objects.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 44.6.6 unassignBeamSectionOrientation(...)

This method deletes a beam section orientation assignment.

**Path**

```
mdb.models[*name*].parts[*name*].unassignBeamSectionOrientation
```

**Required argument**

*index*

An Int specifying the number of the beam section orientation assignment to be deleted.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 44.6.7 unassignMaterialOrientation(...)

This method deletes a material orientation assignment.

**Path**

```
mdb.models[*name*].parts[*name*].unassignMaterialOrientation
```

**Required argument**

*index*

An Int specifying the number of the material assignment to be deleted.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 44.6.8 unassignRebarOrientation(...)

This method deletes a rebar orientation assignment.

**Path**

```
mdb.models[*name*].parts[*name*].unassignRebarOrientation
```

**Required argument**

*index*

An Int specifying the number of the rebar reference orientation assignment to be deleted.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.



