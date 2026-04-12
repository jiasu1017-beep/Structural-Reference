# 31.6 MeshElementArray object







The MeshElementArray is a sequence of [MeshElement](pt01ch31pyo05.md) objects.

**Access**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].elements
mdb.models[*name*].parts[*name*].allInternalSurfaces[*name*].elements
mdb.models[*name*].parts[*name*].allSets[*name*].elements
mdb.models[*name*].parts[*name*].allSurfaces[*name*].elements
mdb.models[*name*].parts[*name*].elements
mdb.models[*name*].parts[*name*].sets[*name*].elements
mdb.models[*name*].parts[*name*].surfaces[*name*].elements
import assembly
mdb.models[*name*].rootAssembly.allinstances.elements
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].elements
mdb.models[*name*].rootAssembly.allinstances.surfaces[*name*].elements
mdb.models[*name*].rootAssembly.allInternalSets[*name*].elements
mdb.models[*name*].rootAssembly.allInternalSurfaces[*name*].elements
mdb.models[*name*].rootAssembly.allSets[*name*].elements
mdb.models[*name*].rootAssembly.allSurfaces[*name*].elements
mdb.models[*name*].rootAssembly.elements
mdb.models[*name*].rootAssembly.instances[*name*].elements
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].elements
mdb.models[*name*].rootAssembly.instances[*name*].surfaces[*name*].elements
mdb.models[*name*].rootAssembly.modelInstances[*i*].elements
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].elements
mdb.models[*name*].rootAssembly.modelInstances[*i*].surfaces[*name*]\
.elements
mdb.models[*name*].rootAssembly.sets[*name*].elements
mdb.models[*name*].rootAssembly.surfaces[*name*].elements
```

### 31.6.1 MeshElementArray(...)

This method creates a MeshElementArray object.

**Path**

```
mesh.MeshElementArray
```

**Required argument**

*elements*

A list of [MeshElement](pt01ch31pyo05.md)objects.

**Optional arguments**

None.

**Return value**

A MeshElementArray object.

**Exceptions**

None.

### 31.6.2 getFromLabel(...)

This method returns the object in the MeshElementArray with the given label.

**Required argument**

*label*

An Int specifying the label of the object.

**Optional arguments**

None.

**Return value**

A [MeshElement](pt01ch31pyo05.md) object.

**Exceptions**

None.

### 31.6.3 getSequenceFromMask(...)

This method returns the objects in the MeshElementArray identified using the specified *mask*. This command is generated when the [JournalOptions](pt01ch47pyo06.md) are set to COMPRESSEDINDEX. When a large number of objects are involved, this method is highly efficient.

**Required argument**

*mask*

A String specifying the object or objects.

**Optional arguments**

None.

**Return value**

A MeshElementArray object.

**Exceptions**

None.

### 31.6.4 getMask()

This method returns a string specifying the object or objects.

**Arguments**

None.

**Return value**

A String specifying the object or objects.

**Exceptions**

None.

### 31.6.5 getByBoundingBox(...)

This method returns an array of element objects that lie within the specified bounding box.

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

A MeshElementArray object, which is a sequence of [MeshElement](pt01ch31pyo05.md) objects. 					 

**Exceptions**

None.

### 31.6.6 getByBoundingCylinder(...)

This method returns an array of element objects that lie within the specified bounding cylinder.

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

A MeshElementArray object, which is a sequence of [MeshElement](pt01ch31pyo05.md) objects. 					 

**Exceptions**

None.

### 31.6.7 getByBoundingSphere(...)

This method returns an array of element objects that lie within the specified bounding sphere.

**Required arguments**

*center*

A tuple of the X-, Y-, and Z-coordinates of the center of the sphere. 								 

*radius*

A float specifying the radius of the sphere. 								 

**Optional arguments**

None.

**Return value**

A MeshElementArray object, which is a sequence of [MeshElement](pt01ch31pyo05.md) objects. 					 

**Exceptions**

None.

### 31.6.8 getBoundingBox()

This method returns a dictionary of two tuples representing minimum and maximum boundary 						 values of the bounding box of the minimum size containing the element sequence. 					 

**Arguments**

None.

**Return value**

A Dictionary object with the following items:

 *low*: a tuple of three floats representing the minimum x, y, and z boundary values of the bounding box.                   

 *high*: a tuple of three floats representing the maximum x, y, and z boundary values of the bounding box.                   

**Exceptions**

None.

### 31.6.9 sequenceFromLabels(...)

This method returns the objects in the MeshElementArray identified using the specified labels. 

**Required argument**

*labels*

A sequence of Ints specifying the labels.

**Optional arguments**

None.

**Return value**

A MeshElementArray object.

**Exceptions**

An exception occurs if the resulting sequence is empty.

```
Error: The mask results in an empty sequence
```

### 31.6.10 Members

The MeshElementArray object has no members.




