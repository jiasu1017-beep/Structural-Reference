# 40.16 OdbDataStep object







The OdbDataStep object.

**Access**

```
import visualization
session.odbData[*name*].steps[*i*]
```

### 40.16.1 setValues(...)

This method modifies the OdbDataStep object.

**Required argument**

*activateFrames*

A Boolean specifying whether to activate all the frames in the step.

**Optional argument**

*update*

A Boolean specifying whether to update the model. The default value is ON 

**Return value**

None

**Exceptions**

None.

### 40.16.2 Members

The OdbDataStep object has the following member:

*frames*

An [OdbDataFrameArray](pt01ch40pyo11.md) object specifying the list of frames. The list is read-only.




