# 45.6 Skin object







The Skin object stores information on skin reinforcements created on entities.

**Access**

```
import part
mdb.models[*name*].parts[*name*].skins[*name*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.skins[*name*]
mdb.models[*name*].rootAssembly.instances[*name*].skins[*name*]
mdb.models[*name*].rootAssembly.skins[*name*]
```

### 45.6.1 Skin(...)

This method creates a skin from a sequence of objects in a model database. At least one of the optional arguments needs to be specified.

**Path**

```
mdb.models[*name*].parts[*name*].Skin
```

**Required argument**

*name*

A String specifying the repository key. The default value is an empty string.

**Optional arguments**

*faces*

A sequence of Face objects specifying the faces on which skins should be created. Applicable to three and two dimensional parts.

*edges*

A sequence of Edge objects specifying the edges on which skins should be created. Applicable to axisymmetric parts.

*elementFaces*

A sequence of MeshFace objects specifying the mesh faces on which skins should be created. Applicable to three and two dimensional parts.

*elementEdges*

A sequence of MeshEdge objects specifying the mesh edges on which skins should be created. Applicable to axisymmetric parts.

**Return value**

A Skin object.

**Exceptions**

InvalidNameError.

### 45.6.2 EditSkin(...)

This method modifies underlying entities of the selected skin. At least one of the optional arguments needs to be specified.

**Path**

```
mdb.models[*name*].parts[*name*].EditSkin
```

**Required argument**

*name*

A String specifying the repository key. The default value is an empty string.

**Optional arguments**

*faces*

A sequence of Face objects specifying the faces on which skins should be created. Applicable to three and two dimensional parts.

*edges*

A sequence of Edge objects specifying the edges on which skins should be created. Applicable to axisymmetric parts.

*elementFaces*

A sequence of MeshFace objects specifying the mesh faces on which skins should be created. Applicable to three and two dimensional parts.

*elementEdges*

A sequence of MeshEdge objects specifying the mesh edges on which skins should be created. Applicable to axisymmetric parts.

**Return value**

A Skin object.

**Exceptions**

InvalidNameError.

### 45.6.3 Members

The Skin object has the following members:

*elements*

A [MeshElementArray](pt01ch31pyo05.md) object.

*edges*

An [EdgeArray](pt01ch07pyo03.md) object.

*faces*

A [FaceArray](pt01ch07pyo05.md) object.




