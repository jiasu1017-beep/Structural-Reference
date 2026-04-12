# 42.7 IMAField object







A IMAField is an object used to define material instance name volume fractions for the [MaterialAssignment](pt01ch42pyo11.md) predefined field.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*].fieldList
```

### 42.7.1 Members

The IMAField object can have the following members:

*region*

A [Region](pt01ch45pyo03.md) object specifying the sub-region of the selected part instance to which the volume fractions will be applied.

*discFieldList*

A tuple of Strings specifying the name of the discrete fields that contain the volume fraction data. The length of the tuple corresponds to the number of material instance names, as established by the assigned Eulerian section.




