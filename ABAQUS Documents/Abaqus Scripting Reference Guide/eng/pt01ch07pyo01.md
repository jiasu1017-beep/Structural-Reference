# 7.1 Cell object







Cells are volumetric regions of geometry.

**Access**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].cells[*i*]
mdb.models[*name*].parts[*name*].allSets[*name*].cells[*i*]
mdb.models[*name*].parts[*name*].cells[*i*]
mdb.models[*name*].parts[*name*].sets[*name*].cells[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.cells[*i*]
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.allInternalSets[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.allSets[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].cells[*i*]
mdb.models[*name*].rootAssembly.sets[*name*].cells[*i*]
```

### 7.1.1 getSize(...)

This method returns a Float indicating the volume of the cell.

**Required arguments**

None.

**Optional argument**

*printResults*

A Boolean that determines whether a verbose output is to be printed. The default is True.

**Return value**

A Float.

**Exceptions**

None.

### 7.1.2 getFaces()

This method returns a sequence consisting of the face IDs of the faces which bound the cell.

**Arguments**

None.

**Return value**

A tuple of integers.

**Exceptions**

None.

### 7.1.3 getEdges()

This method returns a sequence consisting of the edge IDs of the edges on the cell.

**Arguments**

None.

**Return value**

A tuple of integers.

**Exceptions**

None.

### 7.1.4 getVertices()

This method returns a sequence consisting of the vertex IDs of the vertices on the cell.

**Arguments**

None.

**Return value**

A tuple of integers.

**Exceptions**

None.

### 7.1.5 getAdjacentCells()

This method returns an array of cell objects that share at least one face of the cell.

**Arguments**

None.

**Return value**

A [CellArray](pt01ch07pyo01.md)                     object which is a sequence of Cell                     objects.

**Exceptions**

None.

### 7.1.6 getNodes()

This method returns an array of node objects that are associated with the cell.

**Arguments**

None.

**Return value**

A [MeshNodeArray](pt01ch31pyo09.md)                       object which is a sequence of [MeshNode](pt01ch31pyo09.md)                     objects.

**Exceptions**

None.

### 7.1.7 getElements()

This method returns an array of element objects that are associated with the cell.

**Arguments**

None.

**Return value**

A [MeshElementArray](pt01ch31pyo05.md)                     object which is a sequence of [MeshElement](pt01ch31pyo05.md)                     objects.

**Exceptions**

None.

### 7.1.8 Members

The Cell object has the following members:

*index*

An Int specifying the index of the cell in the CellArray.

*isReferenceRep*

A Boolean specifying whether the cell belongs to the reference representation of                   the Part or Instance.

*pointOn*

A tuple of Floats specifying the *X*-, *Y*-, and *Z*-coordinates of a point located on the cell.

*featureName*

A tuple of Floats specifying the name of the feature that created this cell.

*instanceName*

A tuple of Floats specifying the name of the part instance for this cell (if applicable).




