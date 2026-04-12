# 27.27 ConnectorForce object







The ConnectorForce object defines a connector force.

The ConnectorForce object is derived from the [Load](pt01ch27pyo01.md) object.

**Access**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.27.1 ConnectorForce(...)

This method creates a ConnectorForce object on a wire region.  Alternatively, the load may also be applied to a wire set referenced from an assembled fastener template model.

**Path**

```
mdb.models[*name*].ConnectorForce
```

**Required arguments**

*name*

A String specifying the load repository key.

*createStepName*

A String specifying the name of the step in which the load is created.

**Optional arguments**

*region*

The wire region to which the load is applied.  This argument is not valid when *fastenerName* and *fastenerSetName* are specified.

*fastenerName*

A String specifying the name of the assembled fastener to which the load will be applied. This argument is not valid when *region* is specified.  When this argument is specified, *fastenerSetName* must also be specified. The default value is an empty string.

*fastenerSetName*

A String specifying the assembled fastener template model set to which the load will be applied. This argument is not valid when *region* is specified.  When this argument is specified, *fastenerName* must also be specified. The default value is an empty string.

*f1*

A Float or a Complex specifying the connector force component in the connector's local 1-direction.

**Note:**Although *f1*, *f2*, and *f3* are optional arguments, at least one of them must be nonzero.

*f2*

A Float or a Complex specifying the connector force component in the connector's local 2-direction.

*f3*

A Float or a Complex specifying the connector force component in the connector's local 3-direction.

*amplitude*

A String or the SymbolicConstant UNSET specifying the name of the amplitude reference. UNSET should be used if the load has no amplitude reference. The default value is UNSET. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

A ConnectorForce object.

**Exceptions**

None.

### 27.27.2 setValues(...)

This method modifies the data for an existing ConnectorForce object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorForce](pt01ch27pyo27.md#ker-connectorforce-connectorforce-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 27.27.3 setValuesInStep(...)

This method modifies the propagating data for an existing ConnectorForce object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the load is modified.

**Optional arguments**

*f1*

A Float, a Complex, or the SymbolicConstant UNCHANGED specifying the connector force component in the connector's local 1-direction. UNCHANGED should be used if the connector force component is propagated from the previous analysis step.

*f2*

A Float, a Complex, or the SymbolicConstant UNCHANGED specifying the connector force component in the connector's local 2-direction. UNCHANGED should be used if the connector force component is propagated from the previous analysis step.

*f3*

A Float, a Complex, or the SymbolicConstant UNCHANGED specifying the connector force component in the connector's local 3-direction. UNCHANGED should be used if the connector force component is propagated from the previous analysis step.

*amplitude*

A String or a SymbolicConstant specifying the name of the amplitude reference. Possible values for the SymbolicConstant are UNCHANGED and FREED. UNCHANGED should be used if the amplitude is propagated from the previous analysis step. FREED should be used if the load is changed to have no amplitude reference. You should provide the *amplitude* argument only if it is valid for the specified step.

**Return value**

None

**Exceptions**

None.

### 27.27.4 Members

The ConnectorForce object can have the following members:

*name*

A String specifying the load repository key.

*fastenerName*

A String specifying the name of the assembled fastener to which the load will be applied. This argument is not valid when *region* is specified.  When this argument is specified, *fastenerSetName* must also be specified. The default value is an empty string.

*fastenerSetName*

A String specifying the assembled fastener template model set to which the load will be applied. This argument is not valid when *region* is specified.  When this argument is specified, *fastenerName* must also be specified. The default value is an empty string.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the load is applied.




