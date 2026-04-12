# 21.4 DiscreteField object







The DiscreteField object defines a varying field whose values correspond to distinct points within a domain.

The DiscreteField object is derived from the [Field](pt01ch21pyo01.md) object.

**Access**

```
import fields
mdb.models[*name*].discreteFields[*name*]
```

### 21.4.1 DiscreteField(...)

This method creates a DiscreteField object.

**Path**

```
mdb.models[*name*].DiscreteField
```

**Required arguments**

*name*

A String specifying the repository key.

*defaultValues*

A sequence of Floats specifying a sequence of floats specifying the default values. 

*fieldType*

A SymbolicConstant or an Int specifying the type of data represented by this discrete field. Possible values are SCALAR, ORIENTATION, and PRESCRIBEDCONDITION_DOF.

**Optional arguments**

*location*

A SymbolicConstant or an Int specifying the location of the domain data. Possible values are NODES and ELEMENTS. The default value is NODES.

*dataWidth*

An Int specifying the width of the supplied data. The default value is 1.

*data*

A [DataTableArray](pt01ch21pyo03.md) object.

*description*

A String specifying the description of the field. The default value is an empty string.

*orientationType*

A SymbolicConstant specifying the type of the system being described by a discrete field used for an orientation. Possible values are CARTESIAN, CYLINDRICAL, and SPHERICAL. The default value is CARTESIAN.

*partLevelOrientation*

A Boolean specifying whether or not the orientations are described in terms of part level coordinates. The default value is OFF.

**Return value**

A DiscreteField object.

**Exceptions**

AbaqusException.

### 21.4.2 DiscreteFieldByVolumeFraction(...)

This method creates a DiscreteField object that represents the volume fraction of each element of an Eulerian Instance that is occupied by a reference instance.

**Path**

```
mdb.models[*name*].rootAssembly.DiscreteFieldByVolumeFraction
```

**Required arguments**

*name*

A String specifying the repository key.

*eulerianInstance*

A [PartInstance](pt01ch06pyo04.md) object specifying the elements for which volume fraction values will be computed.

*referenceInstance*

A [PartInstance](pt01ch06pyo04.md) object specifying the region that either contains material or is empty of material.

**Optional arguments**

*accuracy*

A Symbolic Constant specifying the level of accuracy that will be used in computing volume fractions.  Possible values are LOW, MEDIUM, or HIGH. The default value is MEDIUM.

*materialLocation*

A Symbolic Constant indicating whether the material is inside or outside the *referenceInstance*. Possible values are INSIDE or OUTSIDE. The default value is INSIDE.

*description*

A String specifying the description of the field. The default value is an empty string.

*scaleFactor*

A float specifying the fraction of the volume that is occupied by the *referenceInstance.* Valid values are between 0 and 1.

**Return value**

A DiscreteField object.

**Exceptions**

AbaqusException.

### 21.4.3 DiscreteFieldFromAnalytic(...)

This method creates a DiscreteField object from a [AnalyticalField](pt01ch21pyo02.md) object.

**Path**

```
mdb.models[*name*].DiscreteFieldFromAnalytic
```

**Required arguments**

*name*

A String specifying the repository key.

*location*

A SymbolicConstant or an Int specifying the location of the domain data. Possible values are NODES and ELEMENTS. The default value is NODES.

*analyticFieldName*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) containing the source data.

*region*

A [Region](pt01ch45pyo03.md) object for the field.

**Optional arguments**

None.

**Return value**

A DiscreteField object.

**Exceptions**

AbaqusException.

### 21.4.4 setValues(...)

This method modifies the DiscreteField object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DiscreteField](pt01ch21pyo04.md#ker-discretefield-discretefield-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

### 21.4.5 Members

The DiscreteField object has members with the same names and descriptions as the arguments to the [DiscreteField](pt01ch21pyo04.md#ker-discretefield-discretefield-pyc) method.




