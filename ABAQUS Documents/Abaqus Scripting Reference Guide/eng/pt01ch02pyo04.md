# 2.4 AdaptiveMeshDomain object







The AdaptiveMeshDomain object defines the region and controls that govern an Arbitrary Lagrangian Eularian (ALE) style adaptive smoothing mesh domain.

**Access**

```
import step
mdb.models[*name*].steps[*name*].adaptiveMeshDomains[*name*]
```

### 2.4.1 AdaptiveMeshDomain(...)

This method creates an AdaptiveMeshDomain object.

**Path**

```
mdb.models[*name*].steps[*name*].AdaptiveMeshDomain
```

**Required argument**

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the adaptive mesh domain is applied.

**Optional arguments**

*controls*

A String specifying the name of an [AdaptiveMeshControl](pt01ch02pyo03.md) object.

*frequency*

An Int specifying the frequency in increments at which adaptive meshing will be performed. The default value is 10.

*initialMeshSweeps*

An Int specifying the number of mesh sweeps to be performed at the beginning of the first step in which this adaptive mesh definition is active. The default value is 5.

*meshSweeps*

An Int specifying the number of mesh sweeps to be performed in each adaptive mesh increment. The default value is 1.

**Return value**

An AdaptiveMeshDomain object.

**Exceptions**

RangeError.

### 2.4.2 setValues(...)

This method modifies the AdaptiveMeshDomain object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [AdaptiveMeshDomain](pt01ch02pyo04.md#ker-adaptivemeshdomain-adaptivemeshdomain-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 2.4.3 Members

The AdaptiveMeshDomain object has members with the same names and descriptions as the arguments to the [AdaptiveMeshDomain](pt01ch02pyo04.md#ker-adaptivemeshdomain-adaptivemeshdomain-pyc) method.




