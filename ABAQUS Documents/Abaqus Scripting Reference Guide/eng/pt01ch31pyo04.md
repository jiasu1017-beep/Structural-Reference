# 31.4 MeshEdge object







The MeshEdge object refers to an element edge. It has no constructor or members. A MeshEdge object can be accessed via a [MeshEdgeArray](pt01ch31pyo04.md) or a repository on a part or part instance.

**Access**

```
import part
mdb.models[*name*].parts[*name*].elemEdges[*i*]
mdb.models[*name*].parts[*name*].elementEdges[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.elemEdges[*i*]
mdb.models[*name*].rootAssembly.allinstances.elementEdges[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].elemEdges[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].elementEdges[*i*]
```

### 31.4.1 getElements()

This method returns a tuple of elements that share the element edge.

**Arguments**

None.

**Return value**

A tuple of [MeshElement](pt01ch31pyo05.md) objects.

**Exceptions**

None.

### 31.4.2 getElementsViaTopology()

This method returns an array of [MeshElement](pt01ch31pyo05.md) objects                   that are obtained by recursively finding adjacent elements via topology.

**Arguments**

None.

**Return value**

A [MeshElementArray](pt01ch31pyo05.md) object, which is a sequence of [MeshElement](pt01ch31pyo05.md) objects.

**Exceptions**

None.

### 31.4.3 getElemFaces()

This method returns a tuple of unique [MeshFace](pt01ch31pyo08.md) objects that share the element edge.

**Arguments**

None.

**Return value**

A tuple of [MeshFace](pt01ch31pyo08.md) objects.

**Exceptions**

None.

### 31.4.4 getNodes()

This method returns a tuple of nodes on the element edge.

**Arguments**

None.

**Return value**

A tuple of [MeshNode](pt01ch31pyo09.md) objects.

**Exceptions**

None.

### 31.4.5 Members

The MeshEdge object has no members.




