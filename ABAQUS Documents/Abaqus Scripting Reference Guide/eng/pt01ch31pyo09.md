# 31.9 MeshNode object







The MeshNode object refers to a node of a native mesh or an orphan mesh. A MeshNode object can be accessed via a part or part instance using an index that refers to the internal numbering of the `node` repository. The index does not refer to the node label.

**Access**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*].nodes[*i*]
mdb.models[*name*].parts[*name*].allInternalSurfaces[*name*].nodes[*i*]
mdb.models[*name*].parts[*name*].allSets[*name*].nodes[*i*]
mdb.models[*name*].parts[*name*].allSurfaces[*name*].nodes[*i*]
mdb.models[*name*].parts[*name*].nodes[*i*]
mdb.models[*name*].parts[*name*].retainedNodes[*i*]
mdb.models[*name*].parts[*name*].sets[*name*].nodes[*i*]
mdb.models[*name*].parts[*name*].surfaces[*name*].nodes[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.nodes[*i*]
mdb.models[*name*].rootAssembly.allinstances.sets[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.allinstances.surfaces[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.allInternalSets[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.allInternalSurfaces[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.allSets[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.allSurfaces[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].surfaces[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].nodes[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].surfaces[*name*]\
.nodes[*i*]
mdb.models[*name*].rootAssembly.nodes[*i*]
mdb.models[*name*].rootAssembly.sets[*name*].nodes[*i*]
mdb.models[*name*].rootAssembly.surfaces[*name*].nodes[*i*]
```

### 31.9.1 Node(...)

This method creates a node on an orphan mesh part.

**Path**

```
mdb.models[*name*].parts[*name*].Node
```

**Required argument**

*coordinates*

A sequence of three Floats specifying the coordinates of the new node.

**Optional arguments**

*localCsys*

A DatumCsys object specifying the local coordinate system. If unspecified, the global coordinate system will be used.

*label*

An Int specifying the node label.

**Return value**

A MeshNode object. 

**Exceptions**

None.

### 31.9.2 getElemEdges()

This method returns a tuple of element edge objects that share the node.

**Arguments**

None.

**Return value**

A tuple of [MeshEdge](pt01ch31pyo04.md) objects.

**Exceptions**

None.

### 31.9.3 getElemFaces()

This method returns a tuple of element face objects that share the node.

**Arguments**

None.

**Return value**

 A tuple of [MeshFace](pt01ch31pyo08.md) objects.

**Exceptions**

None.

### 31.9.4 getElements()

This method returns a tuple of element objects that share the node.

**Arguments**

None.

**Return value**

 A tuple of [MeshElement](pt01ch31pyo05.md) objects.

**Exceptions**

None.

### 31.9.5 getNodesByFeatureEdge(...)

                 This method returns an array of mesh node objects                  that are obtained by recursively finding adjacent nodes along a feature edge                  that are at an angle of less than or equal to the specified face angle.

**Required argument**

*angle*

                       A float specifying the value of the face angle in degrees.

**Optional arguments**

None.

**Return value**

                  A [MeshNodeArray](pt01ch31pyo09.md) object, which is a sequence of MeshNode objects.

**Exceptions**

None.

### 31.9.6 setValues(...)

This method modifies the MeshNode object.

**Required arguments**

None.

**Optional argument**

*label*

 An Int specifying the node label. This member may only be edited if the node belongs to an orphan mesh part. The specified label must be non-negative and must not be in use by any other node of the same part.

**Return value**

None

**Exceptions**

None.

### 31.9.7 Members

The MeshNode object has the following members:

*label*

An Int specifying the node label.

*instanceName*

A String specifying the name of the part instance that owns this node.

*coordinates*

A tuple of three Floats specifying the coordinates of the new node.




