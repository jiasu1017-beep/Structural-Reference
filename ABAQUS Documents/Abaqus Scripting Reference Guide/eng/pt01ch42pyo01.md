# 42.1 PredefinedField object







The PredefinedField object is the base object for the objects in the `predefined field` repository. The methods and members of the PredefinedField object are common to all objects derived from PredefinedField.

An instance of any PredefinedField object can be obtained through the `predefined field` repository of the [Model](pt01ch33pyo01.md) object. An instance of any PredefinedFieldState object can be obtained through the `predefined field` repository of the [Step](pt01ch49pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.1.1 move(...)

This method moves a specific [PredefinedFieldState](pt01ch42pyo12.md) object from one step to a different step.

**Required arguments**

*fromStepName*

A String specifying the name of the step from which the [PredefinedFieldState](pt01ch42pyo12.md) object is moved.

*toStepName*

A String specifying the name of the step to which the [PredefinedFieldState](pt01ch42pyo12.md) object is moved.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

TextError.

### 42.1.2 resume()

This method resumes the predefined field that was previously suppressed.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 42.1.3 suppress()

This method suppresses the predefined field.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 42.1.4 delete(...)

 This method allows you to delete existing fields.

**Required argument**

*indices*

A sequence of Ints specifying the index of each field to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 42.1.5 Members

The PredefinedField object can have the following members:

*name*

A String specifying the repository key.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the predefined field is applied. *Region* is ignored if the predefined field has an *instances* member available.  *Region* is also ignored if the predefined field has a *distributionType* member available, and *distributionType*=FROM_FILE or FROM_FILE_AND_USER_DEFINED.




