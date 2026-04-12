# 19.12 PointMassInertia object







The PointMassInertia object defines point masses and point rotary inertia on a part or an assembly region.

The PointMassInertia object is derived from the [Inertia](pt01ch19pyo09.md) object.

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.inertias[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.inertias[*name*]
```

### 19.12.1 PointMassInertia(...)

This method creates a PointMassInertia object.

**Path**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.PointMassInertia
mdb.models[*name*].rootAssembly.engineeringFeatures.PointMassInertia
```

**Required arguments**

*name*

A String specifying the repository key.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the mass or rotary inertia is applied.

**Optional arguments**

*mass*

A Float specifying the mass magnitude for isotropic mass.  This parameter cannot be specified when anisotropic mass terms are specified. The default value is 0.0.

*mass1*

A Float specifying the mass in the 1-direction for anisotropic mass.  This parameter cannot be specified when isotropic mass is also specified. The default value is 0.0.

*mass2*

A Float specifying the mass in the 2-direction for anisotropic mass.  This parameter cannot be specified when isotropic mass is also specified. The default value is 0.0.

*mass3*

A Float specifying the mass in the 3-direction for anisotropic mass.  This parameter cannot be specified when isotropic mass is also specified. The default value is 0.0.

*i11*

A Float specifying the rotary inertia about the local 1-axis, ![](../graphics/ker_eqn00019.gif). The default value is 0.0.

*i22*

A Float specifying the rotary inertia about the local 2-axis, ![](../graphics/ker_eqn00021.gif). The default value is 0.0.

*i33*

A Float specifying the rotary inertia about the local 3-axis, ![](../graphics/ker_eqn00057.gif). The default value is 0.0.

*i12*

A Float specifying the product of inertia, ![](../graphics/ker_eqn00020.gif). The default value is 0.0.

*i13*

A Float specifying the product of inertia, ![](../graphics/ker_eqn00058.gif). The default value is 0.0.

*i23*

A Float specifying the product of inertia, ![](../graphics/ker_eqn00059.gif). The default value is 0.0.

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system for the anisotropic mass terms (when specified), and the rotary inertia (when specified). If *localCsys*=`None`, the anisotropic mass and rotary inertia data are defined in the global coordinate system. The default value is `None`.

*alpha*

A Float specifying the alpha damping magnitude. The default value is 0.0.

This argument applies only to Abaqus/Standard analyses.

*composite*

A Float specifying the composite damping magnitude. The default value is 0.0.

This argument applies only to Abaqus/Standard analyses.

**Return value**

A PointMassInertia object.

**Exceptions**

None.

### 19.12.2 setValues(...)

This method modifies the PointMassInertia object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [PointMassInertia](pt01ch19pyo12.md#ker-pointmassinertia-pointmassinertia-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 19.12.3 Members

The PointMassInertia object has members with the same names and descriptions as the arguments to the [PointMassInertia](pt01ch19pyo12.md#ker-pointmassinertia-pointmassinertia-pyc) method.

In addition, the PointMassInertia object has the following member:

*suppressed*

A Boolean specifying whether the inertia is suppressed or not. The default value is OFF.

### 19.12.4 Corresponding analysis keywords

| [*MASS](../key/key-link.md#usb-kws-mmass), [*ROTARY INERTIA](../key/key-link.md#usb-kws-mrotinertia) |
| --- |




