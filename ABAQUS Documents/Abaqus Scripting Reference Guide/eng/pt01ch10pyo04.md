# 10.4 ElasIsoBehavior object







TheElasIsoBehavior               object represents the Elastic Isotropic Behavior type.

**Access**

```
import calibration
mdb.models[*name*].calibrations[*name*].behaviors.elasIsoBehavior
```

### 10.4.1 ElasIsoBehavior(...)

This method creates a ElasIsoBehavior                     object.

**Path**

```
mdb.models[*name*].calibrations[*name*].behaviors.ElasIsoBehavior
```

**Required arguments**

*name*

A String specifying the name of the new behavior.

*typeName*

A String specifying the type of the new Behavior. Values can be "ElasIsoBehavior", "ElasPlasIsoBehavior", "FeFpBehavior" or a user plug-in behavior type. For this object it will be "ElasIsoBehavior"

**Optional arguments**

None.

**Return value**

An ElasIsoBehavior object.

**Exceptions**

InvalidNameError.

### 10.4.2 setValues(...)

This method modifies the data for an existing ElasIsoBehavior object.

**Required arguments**

None.

**Optional arguments**

*E*

Young's modulus.

*nu*

Poisson's ratio.

*ds1Name*

The name of the first data set.

*ds2Name*

The name of the second data set.

*materialName*

Material Name.

**Return value**

None

**Exceptions**

None.

### 10.4.3 Members

The ElasIsoBehavior object has members with the same names and descriptions as the arguments to the [ElasIsoBehavior](pt01ch10pyo04.md#ker-elasisobehavior-elasisobehavior-pyc) method.




