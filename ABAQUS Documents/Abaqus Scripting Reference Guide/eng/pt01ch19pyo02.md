# 19.2 AssembledFastener object







The AssembledFastener object defines an assembled fastener.

The AssembledFastener object is derived from the [Fastener](pt01ch19pyo07.md) object.

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.fasteners[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.fasteners[*name*]
```

### 19.2.1 AssembledFastener(...)

This method creates an AssembledFastener object. Although the constructor is available both for parts and for the assembly, AssembledFastener objects are currently supported only under the assembly.

**Path**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.AssembledFastener
mdb.models[*name*].rootAssembly.engineeringFeatures.AssembledFastener
```

**Required arguments**

*name*

A String specifying the repository key.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region of attachment points to which assembled fasteners are applied.

*templateModel*

A String specifying the name of the template model.

*controlSet*

A [Region](pt01ch45pyo03.md) object specifying the template model control point set. The set must contain a single node or vertex.

*templateSurfaces*

A sequence of Strings specifying the names of the template model surfaces that are referenced by tie or coupling constraints.

*assignedSurfaces*

A sequence of Strings specifying the names of the main model surfaces that will be substituted for the template model constraint surfaces.

*propertyPrefix*

A String specifying the name of the property prefix string. This string will be prepended to every property name as it is copied to the main model from the template model.

**Optional arguments**

*orientMethod*

A SymbolicConstant specifying the method used to orient the virtual instances of the template model at each attachment point. Possible values are NORMALS and CSYS. The default value is NORMALS.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system. If *localCsys*=`None`, the global coordinate system is used. When this member is queried, it returns an Int. The default value is `None`.

This argument applies only when *orientMethod*=CSYS.

*scriptName*

A String specifying the name of the property generation script. The default value is an empty string.

**Return value**

An AssembledFastener object.

**Exceptions**

None.

### 19.2.2 setValues(...)

This method modifies the AssembledFastener object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [AssembledFastener](pt01ch19pyo02.md#ker-assembledfastener-assembledfastener-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 19.2.3 Members

The AssembledFastener object has members with the same names and descriptions as the arguments to the [AssembledFastener](pt01ch19pyo02.md#ker-assembledfastener-assembledfastener-pyc) method.

In addition, the AssembledFastener object has the following member:

*suppressed*

A Boolean specifying whether the fastener is suppressed or not. The default value is OFF.




