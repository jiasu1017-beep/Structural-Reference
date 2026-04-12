# 42.8 IMARegion object







A IMARegion is an object used to define material instance name volume fractions for the [MaterialAssignment](pt01ch42pyo11.md) predefined field.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*].assignmentList
```

### 42.8.1 Members

The IMARegion object can have the following members:

*region*

A [Region](pt01ch45pyo03.md) object specifying the sub-region of the selected part instance to which the volume fractions will be applied.

*fractionList*

A tuple of Floats specifying the volume fractions, per material instance name. The length of the tuple corresponds to the number of material instance names, as established by the assigned Eulerian section.




