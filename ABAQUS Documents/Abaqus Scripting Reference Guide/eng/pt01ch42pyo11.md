# 42.11 MaterialAssignment object







The MaterialAssignment object stores the data for an initial material assignment predefined field, for use with an Eulerian analysis.

The MaterialAssignment object is derived from the [PredefinedField](pt01ch42pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.11.1 MaterialAssignment(...)

This method creates a MaterialAssignment predefined field object.

**Path**

```
mdb.models[*name*].MaterialAssignment
```

**Required arguments**

*name*

A String specifying the repository key.

*instanceList*

A [PartInstanceArray](pt01ch06pyo04.md) object specifying the part instances to which the predefined field is applied. All instances must be assigned the same Eulerian section.

**Optional arguments**

*useFields*

A Boolean specifying whether the volume fraction data will be uniform or defined by discrete fields. The default value is OFF.

*assignmentList*

A sequence of tuples specifying the uniform volume fractions to be assigned. This argument is valid only when *useFields*=FALSE.  Each tuple contains two entries: 
- A [Region](pt01ch45pyo03.md) object.
- A tuple of Floats specifying the uniform volume fraction values. The length of the tuple must match the number of material instance names specified in the Eulerain section assigned to part instances specified by *instanceList*.

*fieldList*

A sequence of tuples specifying the discrete volume fractions to be assigned. This argument is valid only when *useFields*=TRUE.  Each tuple contains two entries: 
- A [Region](pt01ch45pyo03.md) object.
- A tuple of Strings specifying Discrete Field names. The length of the tuple must match the number of material instance names specified in the Eulerain section assigned to part instances specified by *instanceList*.

*colorList*

A sequence of three Ints specifying colors used to display the material instance assignments. This is a sequence of R,G,B colors, where the values are represented by integers between 0 and 255. The default value is an empty sequence.

**Return value**

A MaterialAssignment object.

**Exceptions**

None.

### 42.11.2 setValues(...)

This method modifies the MaterialAssignment object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [MaterialAssignment](pt01ch42pyo11.md#ker-materialassignment-materialassignment-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 42.11.3 Members

The MaterialAssignment object has members with the same names and descriptions as the arguments to the [MaterialAssignment](pt01ch42pyo11.md#ker-materialassignment-materialassignment-pyc) method.

In addition, the MaterialAssignment object can have the following member:

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the predefined field is applied. *Region* is ignored if the predefined field has an *instances* member available.  *Region* is also ignored if the predefined field has a *distributionType* member available, and *distributionType*=FROM_FILE or FROM_FILE_AND_USER_DEFINED.

### 42.11.4 Corresponding analysis keywords

| [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond), TYPE=EULERIAN MATERIAL |
| --- |




