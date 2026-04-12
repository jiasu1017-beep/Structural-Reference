# 19.6 DiscreteFastener object







The DiscreteFastener object defines a discrete fastener.

The DiscreteFastener object is derived from the [Fastener](pt01ch19pyo07.md) object.

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.fasteners[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.fasteners[*name*]
```

### 19.6.1 DiscreteFastener(...)

This method creates a DiscreteFastener object. Although the constructor is available both for parts and for the assembly, DiscreteFastener objects are currently supported only under the assembly.

**Path**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.DiscreteFastener
mdb.models[*name*].rootAssembly.engineeringFeatures.DiscreteFastener
```

**Required arguments**

*name*

A String specifying the repository key.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the fastener is applied.

*influenceRadius*

The SymbolicConstant WHOLE_SURFACE or a Float specifying the coupling influence radius.

**Optional arguments**

*ur1*

A Boolean specifying whether to constrain rotational displacement component about the 1-direction. The default value is ON.

*ur2*

A Boolean specifying whether to constrain rotational displacement component about the 2-direction. The default value is ON.

*ur3*

A Boolean specifying whether to constrain rotational displacement component about the 3-direction. The default value is ON.

*coupling*

A SymbolicConstant specifying the coupling method used to couple the displacement and rotation of each attachment point to the average motion of the surface nodes within the radius of influence from the fastening point. Possible values are CONTINUUM and STRUCTURAL. The default value is CONTINUUM.

*weightingMethod*

A SymbolicConstant specifying the weighting scheme to be used to weight the contribution of the displacements of the surface nodes within the radius of influence to the motion of the fastening point.  UNIFORM, LINEAR, QUADRATIC, and CUBIC indicate uniform, linear decreasing, quadratic polynomial decreasing, and cubic polynomial monotonic decreasing weight distributions. Possible values are UNIFORM, LINEAR, QUADRATIC, and CUBIC. The default value is UNIFORM.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of fastener couplings. If *localCsys*=`None`, couplings are defined in the global coordinate system. When this member is queried, it returns an Int. The default value is `None`.

**Return value**

A DiscreteFastener object.

**Exceptions**

None.

### 19.6.2 setValues(...)

This method modifies the DiscreteFastener object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DiscreteFastener](pt01ch19pyo06.md#ker-discretefastener-discretefastener-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 19.6.3 Members

The DiscreteFastener object has members with the same names and descriptions as the arguments to the [DiscreteFastener](pt01ch19pyo06.md#ker-discretefastener-discretefastener-pyc) method.

In addition, the DiscreteFastener object has the following member:

*suppressed*

A Boolean specifying whether the fastener is suppressed or not. The default value is OFF.

### 19.6.4 Corresponding analysis keywords

| [*COUPLING](../key/key-link.md#usb-kws-mcoupling), [*DISTRIBUTING](../key/key-link.md#usb-kws-mdistributing) |
| --- |




