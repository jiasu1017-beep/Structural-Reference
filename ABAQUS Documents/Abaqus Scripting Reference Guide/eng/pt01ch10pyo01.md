# 10.1 Calibration object







A Calibration               object is the object used to specify a material calibration. The Calibration               object stores the data that is used for specifying materials from test data.

**Access**

```
import calibration
mdb.models[*name*].calibrations[*name*]
```

### 10.1.1 Calibration(...)

This method creates a Calibration                     object.

**Path**

```
mdb.models[*name*].Calibration
```

**Required argument**

*name*

A String specifying the name of the new calibration.

**Optional arguments**

None.

**Return value**

A Calibration object.

**Exceptions**

InvalidNameError.

### 10.1.2 Members

The Calibration object has members with the same names and descriptions as the arguments to the [Calibration](pt01ch10pyo01.md#ker-calibration-calibration-pyc) method.

In addition, the Calibration object can have the following members:

*dataSets*

A [DataSet](pt01ch10pyo03.md) object.

*behaviors*

A [Behavior](pt01ch10pyo02.md) object.




