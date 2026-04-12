# 31.8 MeshFace object







The MeshFace object refers to an element face. It has no constructor or members. A MeshFace object can be accessed via a [MeshFaceArray](pt01ch31pyo08.md) or a repository on a part or part instance.

**Access**

```
import part
mdb.models[*name*].parts[*name*].elementFaces[*i*]
mdb.models[*name*].parts[*name*].elemFaces[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.elementFaces[*i*]
mdb.models[*name*].rootAssembly.allinstances.elemFaces[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].elementFaces[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].elemFaces[*i*]
```

### 31.8.1 getElemEdges()

This method returns a tuple of unique element edges on the element face.

**Arguments**

None.

**Return value**

A tuple of [MeshEdge](pt01ch31pyo04.md) objects.

**Exceptions**

None.

### 31.8.2 getElements()

This method returns a tuple of elements that share the element face.

**Arguments**

None.

**Return value**

A tuple of [MeshElement](pt01ch31pyo05.md) objects.

**Exceptions**

None.

### 31.8.3 getNodes()

This method returns a tuple of nodes on the element face.

**Arguments**

None.

**Return value**

A tuple of [MeshNode](pt01ch31pyo09.md) objects.

**Exceptions**

None.

### 31.8.4 getNodesByFaceAngle(...)

This method returns an array of mesh node objects  					 that are obtained by recursively finding adjacent element faces  					 that are at an angle of less than or equal to the specified angle.

**Required argument**

*angle*

 A float specifying the value of the face angle.

**Optional arguments**

None.

**Return value**

 A [MeshNodeArray](pt01ch31pyo09.md) object, which is a sequence of [MeshNode](pt01ch31pyo09.md) objects.

**Exceptions**

None.

### 31.8.5 getElemFacesByFaceAngle(...)

This method returns an array of element face objects  					 that are obtained by recursively finding adjacent element faces  					 that are at an angle of less than or equal to the specified angle.

**Required argument**

*angle*

A float specifying the value of the face angle.

**Optional arguments**

None.

**Return value**

A [MeshFaceArray](pt01ch31pyo08.md) object, which is a sequence of MeshFace objects.

**Exceptions**

None.

### 31.8.6 getElemEdgesByFaceAngle(...)

                  This method returns an array of element edge objects                   that are obtained by recursively finding adjacent element edges                   that are at an angle of less than or equal to the specified face angle.

**Required argument**

*angle*

                        A float specifying the value of the face angle in degrees.

**Optional arguments**

None.

**Return value**

A [MeshEdgeArray](pt01ch31pyo04.md) object, which is a sequence of [MeshEdge](pt01ch31pyo04.md) objects.

**Exceptions**

None.

### 31.8.7 getElementsByFaceAngle(...)

This method returns an array of mesh Element objects  					 that are obtained by recursively finding adjacent element faces  					 that are at an angle of less than or equal to the specified angle.

**Required argument**

*angle*

A float specifying the value of the face angle.

**Optional arguments**

None.

**Return value**

A [MeshElementArray](pt01ch31pyo05.md) object, which is a sequence of [MeshElement](pt01ch31pyo05.md) objects.

**Exceptions**

None.

### 31.8.8 getElemFacesByLimitingAngle(...)

                  This method returns an array of element edge objects                   that are obtained by recursively finding adjacent element faces                   that are at an angle of less than or equal to the specified face angle with the seed face.

**Required argument**

*angle*

                        A float specifying the value of the face angle in degrees.

**Optional arguments**

None.

**Return value**

                  A [MeshFaceArray](pt01ch31pyo08.md) object, which is a sequence of MeshFace objects.

**Exceptions**

None.

### 31.8.9 getElementsViaTopology()

This method returns an array of mesh Element objects                   that are obtained by recursively finding adjacent elements via topology.

**Arguments**

None.

**Return value**

A [MeshElementArray](pt01ch31pyo05.md) object, which is a sequence of [MeshElement](pt01ch31pyo05.md) objects.

**Exceptions**

None.

### 31.8.10 getElemFacesByLayer()

This method returns an array of element face objects                   that are obtained by recursively finding adjacent element faces by layer.

**Required argument**

*numLayer*

 A int specifying the value of the number of layers.

**Optional arguments**

None.

**Return value**

A [MeshFaceArray](pt01ch31pyo08.md) object, which is a sequence of MeshFace objects.

**Exceptions**

None.

### 31.8.11 Members

The MeshFace object has the following members:

*label*

An Int specifying an Int specifying the element label.

*face*

An Int specifying a symbolic constant specifying the side of the element.




