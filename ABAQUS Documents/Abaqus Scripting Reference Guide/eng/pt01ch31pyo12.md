# 31.12 MeshEdgeArray object







The MeshEdgeArray is a sequence of [MeshEdge](pt01ch31pyo04.md) objects.

**Access**

```
import part
mdb.models[*name*].parts[*name*].elementEdges
import assembly
mdb.models[*name*].rootAssembly.allinstances.elementEdges
mdb.models[*name*].rootAssembly.instances[*name*].elementEdges
```

### 31.12.1 MeshEdgeArray(...)

This method creates a MeshEdgeArray object.

**Path**

```
mesh.MeshEdgeArray
```

**Required argument**

*edges*

A list of [MeshEdge](pt01ch31pyo04.md)objects.

**Optional arguments**

None.

**Return value**

A MeshEdgeArray object.

**Exceptions**

None.

### 31.12.2 getSequenceFromMask(...)

This method returns the objects in the MeshEdgeArray identified using the specified *mask*. When large number of objects are involved, this method is highly efficient.

**Required argument**

*mask*

A String specifying the object or objects.

**Optional arguments**

None.

**Return value**

A MeshEdgeArray object.

**Exceptions**

An exception occurs if the resulting sequence is empty.

```
Error: The mask results in an empty sequence
```

### 31.12.3 getMask()

This method returns a string specifying the object or objects.

**Arguments**

None.

**Return value**

A String specifying the object or objects.

**Exceptions**

None.

### 31.12.4 Members

The MeshEdgeArray object has no members.




