# 51.8 Restart object







The Restart object defines a restart request.

**Access**

```
import step
mdb.models[*name*].steps[*name*].restart
```

### 51.8.1 Restart(...)

This method creates a restart request.

**Path**

```
mdb.models[*name*].steps[*name*].Restart
```

**Required arguments**

None.

**Optional arguments**

*numberIntervals*

An Int specifying the number of intervals during the step at which restart information will be written. The default value is 0. The default value is 1.

*timeMarks*

A Boolean specifying whether to use exact time marks for writing during an analysis. The default value is OFF. The default value is OFF.

*overlay*

A Boolean specifying that only one increment per step should be retained on the restart file, thus minimizing the size of the restart file. The default value is OFF. The default value is ON.

*frequency*

An Int specifying the increments at which restart information will be written. The default value is 0. The default value is 0.

This argument applies only to Abaqus/Standard analyses.

**Return value**

A Restart object.

**Exceptions**

RangeError.

### 51.8.2 setValues(...)

This method modifies the Restart object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Restart](pt01ch51pyo08.md#ker-restart-restart-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 51.8.3 Members

The Restart object has members with the same names and descriptions as the arguments to the [Restart](pt01ch51pyo08.md#ker-restart-restart-pyc) method.

### 51.8.4 Corresponding analysis keywords

| [*RESTART](../key/key-link.md#usb-kws-mrestart) |
| --- |




