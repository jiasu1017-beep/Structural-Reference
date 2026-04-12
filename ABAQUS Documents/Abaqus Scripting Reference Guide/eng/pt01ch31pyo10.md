# 31.10 MeshNodeArray object







The MeshNodeArray is a sequence of [MeshNode](pt01ch31pyo09.md) objects.

**Access**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].nodes
mdb.models[*name*].parts[*name*].allInternalSurfaces[*name*].nodes
mdb.models[*name*].parts[*name*].allSets[*name*].nodes
mdb.models[*name*].parts[*name*].allSurfaces[*name*].nodes
mdb.models[*name*].parts[*name*].nodes
mdb.models[*name*].parts[*name*].retainedNodes
mdb.models[*name*].parts[*name*].sets[*name*].nodes
mdb.models[*name*].parts[*name*].surfaces[*name*].nodes
import assembly
mdb.models[*name*].rootAssembly.allinstances.nodes
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].nodes
mdb.models[*name*].rootAssembly.allinstances.surfaces[*name*].nodes
mdb.models[*name*].rootAssembly.allInternalSets[*name*].nodes
mdb.models[*name*].rootAssembly.allInternalSurfaces[*name*].nodes
mdb.models[*name*].rootAssembly.allSets[*name*].nodes
mdb.models[*name*].rootAssembly.allSurfaces[*name*].nodes
mdb.models[*name*].rootAssembly.instances[*name*].nodes
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].nodes
mdb.models[*name*].rootAssembly.instances[*name*].surfaces[*name*].nodes
mdb.models[*name*].rootAssembly.modelInstances[*i*].nodes
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].nodes
mdb.models[*name*].rootAssembly.modelInstances[*i*].surfaces[*name*].nodes
mdb.models[*name*].rootAssembly.nodes
mdb.models[*name*].rootAssembly.sets[*name*].nodes
mdb.models[*name*].rootAssembly.surfaces[*name*].nodes
```

### 31.10.1 MeshNodeArray(...)

This method creates a MeshNodeArray object.

**Path**

```
mesh.MeshNodeArray
```

**Required argument**

*nodes*

A list of [MeshNode](pt01ch31pyo09.md) objects.

**Optional arguments**

None.

**Return value**

A MeshNodeArray object.

**Exceptions**

None.

### 31.10.2 getFromLabel(...)

This method returns the object in the MeshNodeArray with the given label.

**Required argument**

*label*

An Int specifying the label of the object.

**Optional arguments**

None.

**Return value**

A [MeshNode](pt01ch31pyo09.md) object.

**Exceptions**

None.

### 31.10.3 getSequenceFromMask(...)

This method returns the objects in the MeshNodeArray identified using the specified *mask*. This command is generated when the [JournalOptions](pt01ch47pyo06.md) are set to COMPRESSEDINDEX. When a large number of objects are involved, this method is highly efficient.

**Required argument**

*mask*

A String specifying the object or objects.

**Optional arguments**

None.

**Return value**

A MeshNodeArray object.

**Exceptions**

None.

### 31.10.4 getMask()

This method returns a string specifying the object or objects.

**Arguments**

None.

**Return value**

A String specifying the object or objects.

**Exceptions**

None.

### 31.10.5 getByBoundingBox(...)

This method returns an array of nodes that lie within the specified bounding box.

**Required arguments**

None.

**Optional arguments**

*xMin*

A float specifying the minimum X boundary of the bounding box.

*yMin*

A float specifying the minimum Y boundary of the bounding box.

*zMin*

A float specifying the minimum Z boundary of the bounding box.

*xMax*

A float specifying the maximum X boundary of the bounding box.

*yMax*

A float specifying the maximum Y boundary of the bounding box.

*zMax*

A float specifying the maximum Z boundary of the bounding box.

**Return value**

A MeshNodeArray object, which is a sequence of [MeshNode](pt01ch31pyo09.md) objects. 					 

**Exceptions**

None.

### 31.10.6 getByBoundingCylinder(...)

This method returns an array of node objects that lie within the specified bounding cylinder.

**Required arguments**

*center1*

A tuple of the X-, Y-, and Z-coordinates of the center of the first end of the cylinder.

*center2*

A tuple of the X-, Y-, and Z-coordinates of the center of the second end of the cylinder.

*radius*

A float specifying the radius of the cylinder.

**Optional arguments**

None.

**Return value**

A MeshNodeArray object, which is a sequence of [MeshNode](pt01ch31pyo09.md) objects. 					 

**Exceptions**

None.

### 31.10.7 getByBoundingSphere(...)

This method returns an array of node objects that lie within the specified bounding sphere.

**Required arguments**

*center*

A tuple of the X-, Y-, and Z-coordinates of the center of the sphere.

*radius*

A float specifying the radius of the sphere.

**Optional arguments**

None.

**Return value**

A MeshNodeArray object, which is a sequence of [MeshNode](pt01ch31pyo09.md) objects. 					 

**Exceptions**

None.

### 31.10.8 getBoundingBox()

This method returns a dictionary of two tuples representing minimum and maximum boundary values of the bounding box of the minimum size containing the node sequence.

**Arguments**

None.

**Return value**

A Dictionary object with the following items:

 *low*: a tuple of three floats representing the minimum x, y and z boundary values of the bounding box.

 *high*: a tuple of three floats representing the maximum x, y and z boundary values of the bounding box.

**Exceptions**

None.

### 31.10.9 sequenceFromLabels(...)

This method returns the objects in the MeshNodeArray identified using the specified labels.

**Required argument**

*labels*

A sequence of Ints specifying the labels.

**Optional arguments**

None.

**Return value**

A MeshNodeArray object.

**Exceptions**

An exception occurs if the resulting sequence is empty.

```
Error: The mask results in an empty sequence
```

### 31.10.10 Members

The MeshNodeArray object has no members.




