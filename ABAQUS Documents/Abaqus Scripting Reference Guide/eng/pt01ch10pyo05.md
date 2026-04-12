# 10.5 ElasPlasIsoBehavior object







TheElasPlasIsoBehavior               object represents the Elastic Isotropic Behavior type.

**Access**

```
import calibration
mdb.models[*name*].calibrations[*name*].behaviors.elasPlasIsoBehavior
```

### 10.5.1 ElasPlasIsoBehavior(...)

This method creates a ElasPlasIsoBehavior                     object.

**Path**

```
mdb.models[*name*].calibrations[*name*].behaviors.ElasPlasIsoBehavior
```

**Required arguments**

*name*

A String specifying the name of the new behavior.

*typeName*

A String specifying the type of the new Behavior. Values can be "ElasIsoBehavior", "ElasPlasIsoBehavior", "FeFpBehavior" or a user plug-in behavior type. For this object it will be "ElasPlasIsoBehavior"

**Optional arguments**

None.

**Return value**

An ElasPlasIsoBehavior object.

**Exceptions**

InvalidNameError.

### 10.5.2 setValues(...)

This method modifies the data for an existing ElasPlasIsoBehavior object.

**Required arguments**

None.

**Optional arguments**

*yieldPoint*

Stress/strain value for the material yield point.

*ultimatePoint*

Stress/strain value for the material ultimate point.

*plasticPoints*

Stress/strain values for the plastic portion of material curve.

*PoissonsRatio*

Poisson's Ratio.

*elasticModulus*

Young's Modulus for the elastic portion of the material curve.

*ds1Name*

Name of the first data set.

*ds2Name*

Name of the second data set.

*materialName*

Name of the material.

*plasticPointsRange*

Extent of the material plastic points.

*name*

Name of the behavior.

**Return value**

None

**Exceptions**

None.

### 10.5.3 Members

The ElasPlasIsoBehavior object has members with the same names and descriptions as the arguments to the [ElasPlasIsoBehavior](pt01ch10pyo05.md#ker-elasplasisobehavior-elasplasisobehavior-pyc) method.




