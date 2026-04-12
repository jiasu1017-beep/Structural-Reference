# 10.3 DataSet object







The DataSet               object specifies material test data.

**Access**

```
import calibration
mdb.models[*name*].calibrations[*name*].dataSets
```

### 10.3.1 DataSet(...)

This method creates a DataSet                     object.

**Path**

```
mdb.models[*name*].calibrations[*name*].DataSet
```

**Required arguments**

*name*

A String specifying the name of the new dataset.

*data*

A sequence of pairs of Floats specifying data set type pairs. Possible values are for stress/strain, force/displacement, or transverse strain/axial strain pairs.

**Optional arguments**

*type*

A String specifying the type of the new dataset. Values can be "STRESS/STRAIN", "FORCE/DISPLACEMENT", or "AXIALSTRAIN/TRANSVERSESTRAIN". The default value is "STRESS/STRAIN".

*form*

A String specifying the form of the new dataset. Values can be "NOMINAL" or "TRUE". The default value is "NOMINAl".

**Return value**

A DataSet object.

**Exceptions**

InvalidNameError.

### 10.3.2 Members

The DataSet object has members with the same names and descriptions as the arguments to the [DataSet](pt01ch10pyo03.md#ker-dataset-dataset-pyc) method.




