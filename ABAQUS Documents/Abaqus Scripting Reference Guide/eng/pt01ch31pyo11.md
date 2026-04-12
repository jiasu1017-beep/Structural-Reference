# 31.11 MeshFaceArray object







The MeshFaceArray is a sequence of [MeshFace](pt01ch31pyo08.md) objects.

**Access**

```
import part
mdb.models[*name*].parts[*name*].elementFaces
import assembly
mdb.models[*name*].rootAssembly.allinstances.elementFaces
mdb.models[*name*].rootAssembly.instances[*name*].elementFaces
```

### 31.11.1 MeshFaceArray(...)

This method creates a MeshFaceArray object.

**Path**

```
mesh.MeshFaceArray
```

**Required argument**

*faces*

A list of [MeshFace](pt01ch31pyo08.md)objects.

**Optional arguments**

None.

**Return value**

A MeshFaceArray object.

**Exceptions**

None.

### 31.11.2 getSequenceFromMask(...)

This method returns the objects in the MeshFaceArray identified using the specified *mask*. When large number of objects are involved, this method is highly efficient.

**Required argument**

*mask*

A String specifying the object or objects.

**Optional arguments**

None.

**Return value**

A MeshFaceArray object.

**Exceptions**

An exception occurs if the resulting sequence is empty.

```
Error: The mask results in an empty sequence
```

### 31.11.3 getMask()

This method returns a string specifying the object or objects.

**Arguments**

None.

**Return value**

A String specifying the object or objects.

**Exceptions**

None.

### 31.11.4 Members

The MeshFaceArray object has no members.




