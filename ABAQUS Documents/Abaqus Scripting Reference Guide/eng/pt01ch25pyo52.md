# 25.52 ModelChange object







The ModelChange object defines model change interactions for element removal and reactivation.

The ModelChange object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.52.1 ModelChange(...)

This method creates a ModelChange object.

**Path**

```
mdb.models[*name*].ModelChange
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the ModelChange object is created.

**Optional arguments**

*isRestart*

A Boolean specifying whether this interaction is being used solely to indicate that model change may be required in a subsequent restart analysis (either for elements or contact pairs). The default value is OFF.

*regionType*

A SymbolicConstant specifying the region selection type. This argument is valid only when *isRestart*=False. Possible values are GEOMETRY, SKINS, STRINGERS, and ELEMENTS. The default value is GEOMETRY.

*region*

A [Region](pt01ch45pyo03.md) object specifying the elements to be removed or reactivated. This argument is valid only when *isRestart*=False.

*activeInStep*

A Boolean specifying whether elements are being removed or reactivated. This argument is valid only when *isRestart*=False. The default value is OFF.

*includeStrain*

A Boolean specifying whether stress/displacement elements are reactivated with strain. This argument is valid only when *isRestart*=False and when *activeInStep*=True. The default value is OFF.

**Return value**

A ModelChange object.

**Exceptions**

None.

### 25.52.2 setValues(...)

This method modifies the data for an existing ModelChange object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ModelChange](pt01ch25pyo52.md#ker-modelchange-modelchange-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.52.3 setValuesInStep(...)

This method modifies the propagating data of an existing ModelChange object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the interaction is modified.

**Optional arguments**

*activeInStep*

A Boolean specifying whether elements are being removed or reactivated. This argument is valid only when *isRestart*=False. The default value is OFF.

*includeStrain*

A Boolean specifying whether stress/displacement elements are reactivated with strain. This argument is valid only when *isRestart*=False and when *activeInStep*=True. The default value is OFF.

**Return value**

None

**Exceptions**

None.

### 25.52.4 Members

The ModelChange object has members with the same names and descriptions as the arguments to the [ModelChange](pt01ch25pyo52.md#ker-modelchange-modelchange-pyc) method.

### 25.52.5 Corresponding analysis keywords

| [*MODEL CHANGE](../key/key-link.md#usb-kws-hmodelchange), TYPE=ELEMENT |
| --- |
| [*MODEL CHANGE](../key/key-link.md#usb-kws-hmodelchange), ACTIVATE |




