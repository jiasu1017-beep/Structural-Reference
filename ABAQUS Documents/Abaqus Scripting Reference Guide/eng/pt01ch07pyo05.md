# 7.5 Face object







Faces are two-dimensional regions of geometry.

**Access**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].allInternalSurfaces[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].allSets[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].allSurfaces[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].sets[*name*].faces[*i*]
mdb.models[*name*].parts[*name*].surfaces[*name*].faces[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.faces[*i*]
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.allinstances.surfaces[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.allInternalSets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.allInternalSurfaces[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.allSets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.allSurfaces[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].surfaces[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].surfaces[*name*]\
.faces[*i*]
mdb.models[*name*].rootAssembly.sets[*name*].faces[*i*]
mdb.models[*name*].rootAssembly.surfaces[*name*].faces[*i*]
```

### 7.5.1 getCentroid()

This method returns the centroid of a face.

**Arguments**

None.

**Return value**

A sequence of Floats specifying the *X*-, *Y*-, and *Z*-coordinates of the centroid of the face.

**Exceptions**

None.

### 7.5.2 getCurvature(...)

This method returns information about the curvature at a location on the face.

**Required arguments**

*point*

A tuple specifying the *X*-, *Y*-, and *Z* coordinates of the point where the curvature is desired. If the *point*                                does not lie on the face it will be projected onto the face. This argument and *uParam*                                and *vParam*                                are mutually exclusive.

*uParam*

A Float specifying the normalized *U*                                parameter value at which the curvature is to be computed. This value must lie between (0,1). *vParam*                                must also be specified. This argument is mutually exclusive with *point*.

*vParam*

A Float specifying the normalized *V*                                parameter value at which the curvature is to be computed. This value must lie between (0,1).

**Optional arguments**

None.

**Return value**

A dictionary with keys 'evaluationPoint', 'principalAxis1', 'principalAxis2', 'curvature1', 'curvature2' and 'gaussianCurvature'. Where the evaluationPoint specifies the location at which the curvature was evaluated. 'principalAxis1' and 'principalAxis2' refer to the vectors specifying the two principal axes of the face. 'curvature1' and 'curvature2' specify the curvatures along the two principal axes.

**Exceptions**

None.

### 7.5.3 getElements()

This method returns an array of element objects that are associated with the face.

**Arguments**

None.

**Return value**

A [MeshElementArray](pt01ch31pyo05.md)                       object which is a sequence of [MeshElement](pt01ch31pyo05.md)                       objects.

**Exceptions**

None.

### 7.5.4 getElementFaces(...)

This method returns an array of mesh face objects. Each mesh face object contains the element label and the side of the element                           that lies on the geometric face.

**Required arguments**

None.

**Optional argument**

*faceSide*

A symbolic constant specifying the side of the geometric face of a solid from which the element faces should be retrieved. Possible values are *SIDE1*, *SIDE2*, and *BOTH_SIDES*. The default value is *BOTH_SIDES*. For shell faces this option is ignored.

**Return value**

A [MeshFaceArray](pt01ch31pyo08.md)                     object which is a sequence of [MeshFace](pt01ch31pyo08.md)                     objects.

**Exceptions**

None.

### 7.5.5 getNodes(...)

This method returns an array of mesh node objects. Each mesh node object contains the label of the node that lies on the geometric face.

**Required arguments**

None.

**Optional argument**

*faceSide*

A symbolic constant specifying the side of the geometric face of a solid from which the nodes should be retrieved. Possible values are xo*SIDE1*, *SIDE2*, and *BOTH_SIDES*. The default value is *BOTH_SIDES*. For shell faces and for faces with compatible meshes on either sides this option is ignored. Otherwise, the nodes on the specified side(s) of the face are output.   

**Return value**

A [MeshNodeArray](pt01ch31pyo09.md)                       object which is a sequence of [MeshNode](pt01ch31pyo09.md)                       objects.

**Exceptions**

None.

### 7.5.6 getNormal(...)

This method returns the normal to a face at the location specified by the *pointOn*                       member. The normal at a different location on the face can be obtained by specifying the optional *point*                       argument.

**Required arguments**

None.

**Optional argument**

*point*

A tuple specifying the *X*-, *Y*-, and *Z* coordinates of the point where the normal to the face is desired. If the *point*                                does not lie on the face it will be projected onto the face.

**Return value**

A sequence of Floats specifying the *X*-, *Y*-, and *Z*-components of the normal to the face.

**Exceptions**

An exception is raised if the optional argument *point*                          is provided but the point cannot be projected onto the face.

None.

### 7.5.7 getSize(...)

This method returns a Float indicating the area of the face.

**Required arguments**

None.

**Optional argument**

*printResults*

A Bool specifying whether verbose output is printed. The default value is True.

**Return value**

A Float.

**Exceptions**

None.

### 7.5.8 getEdges()

This method returns a sequence consisting of the edge ids of the edges on the face.

**Arguments**

None.

**Return value**

A tuple of integers.

**Exceptions**

None.

### 7.5.9 getVertices()

This method returns a sequence consisting of the vertex ids of the vertices of the face.

**Arguments**

None.

**Return value**

A tuple of integers.

**Exceptions**

None.

### 7.5.10 getCells()

This method returns a sequence consisting of the cell ids of the cells to which this face belongs.

**Arguments**

None.

**Return value**

A tuple of integers.

**Exceptions**

None.

### 7.5.11 getAdjacentFaces()

This method returns an array of face objects that share at least one edge of the face.

**Arguments**

None.

**Return value**

A [FaceArray](pt01ch07pyo05.md)                       object which is a sequence of Face                       objects.

**Exceptions**

None.

### 7.5.12 getFacesByFaceAngle(...)

This method returns an array of Face objects that are obtained by recursively finding adjacent faces that are at an angle of less than or equal to the specified angle.

**Required argument**

*angle*

A float specifying the value of the face angle.

**Optional arguments**

None.

**Return value**

A [FaceArray](pt01ch07pyo05.md)                       object, which is a sequence of Face                       objects.

**Exceptions**

None.

### 7.5.13 getFacesByCurvature()

This method returns an array of Face objects that are obtained by recursively finding adjacent                    faces that share the same curvature.

**Arguments**

None.

**Return value**

A [FaceArray](pt01ch07pyo05.md) object, which is a sequence of Face objects.

**Exceptions**

None.

### 7.5.14 isNormalFlipped()

This method determines whether the normal to the face is flipped from                      its default direction by the use of the `FlipNormal`                       method on a Part object.

**Arguments**

None.

**Return value**

A Boolean value of True if the normal is flipped and False if not.

**Exceptions**

None.

### 7.5.15 Members

The Face object has the following members:

*index*

An Int specifying the index of the face in the FaceArray.

*isReferenceRep*

A Boolean specifying whether the face belongs to the reference representation of                   the Part or Instance.

*pointOn*

A tuple of tuples of Floats specifying the coordinates. For a face of a shell *pointOn*                       specifies the *X*-, *Y*-, and *Z*-coordinates of a point located on the face and the *X*-, *Y*-, and *Z*-components of the normal to the face.

For a face of a solid *pointOn*                       specifies the *X*-, *Y*-, and *Z*-coordinates of a point located on the face.

*featureName*

A tuple of Floats specifying the name of the feature that created this face.

*instanceName*

A tuple of Floats specifying the name of the part instance for this face (if applicable).




