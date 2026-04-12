# 25.62 SelfContactStd object







The SelfContactStd object defines self-contact during an Abaqus/Standard analysis.

The SelfContactStd object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.62.1 SelfContactStd(...)

This method creates a SelfContactStd object.

**Path**

```
mdb.models[*name*].SelfContactStd
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the SelfContactStd object is created.

*surface*

A [Region](pt01ch45pyo03.md) object specifying the surface where self-contact is defined.

*interactionProperty*

A String specifying the name of the [ContactProperty](pt01ch25pyo21.md) object associated with this interaction.

**Optional arguments**

*enforcement*

A SymbolicConstant specifying the discretization method. Possible values are NODE_TO_SURFACE and SURFACE_TO_SURFACE. The default value is SURFACE_TO_SURFACE.

*thickness*

A Boolean specifying whether shell/membrane element thickness is considered. The default value is ON.

This argument in valid only when *enforcement*=SURFACE_TO_SURFACE.

*smooth*

A Float specifying the degree of smoothing used for deformable or rigid master surfaces involved when *enforcement*=NODE_TO_SURFACE. The value given must lie between 0.0 and 0.5. The default value is 0.2.

*contactControls*

A String specifying the name of the [ContactControl](pt01ch25pyo16.md) object associated with this interaction. An empty string indicates that the default contact controls will be used. The default value is an empty string.

**Return value**

A SelfContactStd object.

**Exceptions**

None.

### 25.62.2 setValues(...)

This method modifies the data for an existing SelfContactStd object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SelfContactStd](pt01ch25pyo62.md#ker-selfcontactstd-selfcontactstd-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.62.3 setValuesInStep(...)

This method modifies the propagating data of an existing SelfContactStd object in the specified step.

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

### 25.62.4 Members

The SelfContactStd object has members with the same names and descriptions as the arguments to the [SelfContactStd](pt01ch25pyo62.md#ker-selfcontactstd-selfcontactstd-pyc) method.

In addition, the SelfContactStd object has the following members:

*contactTracking*

A SymbolicConstant specifying the choice of contact tracking algorithm. The STATE tracking algorithm uses only normal projections and is specified by using ONE_CONFIG. The PATH tracking algorithm uses crossing and normal projections and is specified by using TWO_CONFIG. Possible values are ONE_CONFIG and TWO_CONFIG. The default value is TWO_CONFIG.

This argument is valid only when *enforcement*=SURFACE_TO_SURFACE.

*supplementaryContact*

A SymbolicConstant specifying the manner in which mid-face constraints are employed. Possible values are SELECTIVE, NEVER, and ALWAYS. The default value is SELECTIVE.

This argument is valid only when *enforcement*=NODE_TO_SURFACE.




