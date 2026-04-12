# 25.28 ElasticFoundation object







The ElasticFoundation object defines a mechanical foundation.

The ElasticFoundation object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.28.1 ElasticFoundation(...)

This method creates an ElasticFoundation object.

**Path**

```
mdb.models[*name*].ElasticFoundation
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the ElasticFoundation object is created. *createStepName* must be set to 'Initial'.

*surface*

A [Region](pt01ch45pyo03.md) object specifying the surface to which the foundation applies.

*stiffness*

A Float specifying the foundation stiffness per area (or per length for beams).

**Optional arguments**

None.

**Return value**

An ElasticFoundation object.

**Exceptions**

None.

### 25.28.2 setValues(...)

This method modifies the data for an existing ElasticFoundation object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ElasticFoundation](pt01ch25pyo28.md#ker-elasticfoundation-elasticfoundation-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.28.3 setValuesInStep(...)

This method modifies the propagating data of an existing ElasticFoundation object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the interaction is modified.

**Optional argument**

*stiffness*

A Float specifying the foundation stiffness per area (or per length for beams).

**Return value**

None

**Exceptions**

None.

### 25.28.4 Members

The ElasticFoundation object has members with the same names and descriptions as the arguments to the [ElasticFoundation](pt01ch25pyo28.md#ker-elasticfoundation-elasticfoundation-pyc) method.

### 25.28.5 Corresponding analysis keywords

| [*FOUNDATION](../key/key-link.md#usb-kws-mfoundation) |
| --- |




