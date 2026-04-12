# 42.9 InitialState object







The InitialState object stores the data for an initial state predefined field.

The InitialState object is derived from the [PredefinedField](pt01ch42pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.9.1 InitialState(...)

This method creates an InitialState predefined field object.

**Path**

```
mdb.models[*name*].InitialState
```

**Required arguments**

*name*

A String specifying the repository key.

*instances*

A [PartInstanceArray](pt01ch06pyo04.md) object specifying the instances to which the predefined field is applied. 

*fileName*

A String specifying the name of the job that generated the initial state data.

**Optional arguments**

*endStep*

The SymbolicConstant LAST_STEP or an Int specifying the step from which the initial state values are to be read or the SymbolicConstant LAST_STEP. The default value is LAST_STEP.

*endIncrement*

The SymbolicConstant STEP_END or an Int specifying the increment, interval or iteration of the step set in *endStep* or the SymbolicConstant STEP_END. The default value is STEP_END.

*updateReferenceConfiguration*

A Boolean specifying whether to update the reference configuration based on the import data. The default value is OFF.

**Return value**

An InitialState object.

**Exceptions**

None.

### 42.9.2 setValues(...)

This method modifies the InitialState object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [InitialState](pt01ch42pyo09.md#ker-initialstate-initialstate-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 42.9.3 Members

The InitialState object has members with the same names and descriptions as the arguments to the [InitialState](pt01ch42pyo09.md#ker-initialstate-initialstate-pyc) method.

In addition, the InitialState object can have the following member:

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the predefined field is applied. *Region* is ignored if the predefined field has an *instances* member available.  *Region* is also ignored if the predefined field has a *distributionType* member available, and *distributionType*=FROM_FILE or FROM_FILE_AND_USER_DEFINED.

### 42.9.4 Corresponding analysis keywords

| [*INSTANCE](../key/key-link.md#usb-kws-minstance) |
| --- |




