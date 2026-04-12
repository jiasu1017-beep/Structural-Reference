# 25.60 SelfContactExp object







The SelfContactExp object defines self-contact during an Abaqus/Explicit analysis.

The SelfContactExp object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.60.1 SelfContactExp(...)

This method creates a SelfContactExp object.

**Path**

```
mdb.models[*name*].SelfContactExp
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the SelfContactExp object is created.

*surface*

A [Region](pt01ch45pyo03.md) object specifying the surface where self-contact is defined.

*interactionProperty*

A String specifying the name of the [ContactProperty](pt01ch25pyo21.md) object associated with this interaction.

**Optional arguments**

*mechanicalConstraint*

A SymbolicConstant specifying the mechanical constraint formulation. Possible values are KINEMATIC and PENALTY. The default value is KINEMATIC.

*contactControls*

A String specifying the name of the [ContactControl](pt01ch25pyo16.md) object associated with this interaction. An empty string indicates that the default contact controls will be used. The default value is an empty string.

**Return value**

A SelfContactExp object.

**Exceptions**

None.

### 25.60.2 setValues(...)

This method modifies the data for an existing SelfContactExp object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SelfContactExp](pt01ch25pyo60.md#ker-selfcontactexp-selfcontactexp-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.60.3 setValuesInStep(...)

This method modifies the propagating data for an existing SelfContactExp object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the interaction is modified.

**Optional arguments**

*interactionProperty*

A String specifying the name of the [ContactProperty](pt01ch25pyo21.md) object associated with this interaction.

*contactControls*

A String specifying the name of the [ContactControl](pt01ch25pyo16.md) object associated with this interaction. An empty string indicates that the default contact controls will be used. The default value is an empty string.

**Return value**

None

**Exceptions**

None.

### 25.60.4 Members

The SelfContactExp object has members with the same names and descriptions as the arguments to the [SelfContactExp](pt01ch25pyo60.md#ker-selfcontactexp-selfcontactexp-pyc) method.




