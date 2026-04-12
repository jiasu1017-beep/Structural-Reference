# 45.7 Stringer object







The Stringer object stores information on stringer reinforcements created on entities.

**Access**

```
import part
mdb.models[*name*].parts[*name*].stringers[*name*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.stringers[*name*]
mdb.models[*name*].rootAssembly.instances[*name*].stringers[*name*]
mdb.models[*name*].rootAssembly.stringers[*name*]
```

### 45.7.1 Stringer(...)

This method creates a stringer from a sequence of objects in a model database. At least one of the optional arguments needs to be specified.

**Path**

```
mdb.models[*name*].parts[*name*].Stringer
```

**Required argument**

*name*

A String specifying the repository key. The default value is an empty string.

**Optional arguments**

*edges*

A sequence of Edge objects specifying the edges on which stringers should be created. Applicable to three and two dimensional parts.

*elementEdges*

A sequence of MeshEdge objects specifying the mesh edges on which stringers should be created. Applicable to three and two dimensional parts.

**Return value**

A Stringer object.

**Exceptions**

InvalidNameError.

### 45.7.2 EditStringer(...)

This method modifies underlying entities of the selected stringer. At least one of the optional arguments needs to be specified.

**Path**

```
mdb.models[*name*].parts[*name*].EditStringer
```

**Required argument**

*name*

A String specifying the repository key. The default value is an empty string.

**Optional arguments**

*edges*

A sequence of Edge objects specifying the edges on which stringers should be created. Applicable to three and two dimensional parts.

*elementEdges*

A sequence of MeshEdge objects specifying the mesh edges on which stringers should be created. Applicable to three and two dimensional parts.

**Return value**

A Stringer object.

**Exceptions**

InvalidNameError.

### 45.7.3 Members

The Stringer object has the following members:

*elements*

A [MeshElementArray](pt01ch31pyo05.md) object.

*edges*

An [EdgeArray](pt01ch07pyo03.md) object.




