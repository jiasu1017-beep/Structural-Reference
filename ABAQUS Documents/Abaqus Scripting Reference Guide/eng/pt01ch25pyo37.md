# 25.37 FluidExchange object







The FluidExchange object is used to define fluid exchange between two fluid cavities or between a fluid cavity and its environment.

The FluidExchange object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.37.1 FluidExchange(...)

This method creates an FluidExchange object.

**Path**

```
mdb.models[*name*].FluidExchange
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the FluidExchange object is created.

*firstCavity*

A String specifying the first [FluidCavity](pt01ch25pyo34.md) object associated with this interaction.  This will be the only cavity specified if *definition*=TO_ENVIRONMENT.

*interactionProperty*

A String specifying the [FluidExchangeProperty](pt01ch25pyo38.md) object associated with this interaction.

**Optional arguments**

*definition*

A SymbolicConstant specifying the type of fluid exchange to be defined. Possible values are TO_ENVIRONMENT and BETWEEN_CAVITIES. The default value is TO_ENVIRONMENT.

*secondCavity*

A String specifying the second [FluidCavity](pt01ch25pyo34.md) object associated with this interaction.  This argument is applicable only when *definition*=BETWEEN_CAVITIES.

*exchangeArea*

A Float specifying the effective exchange area. The default value is 1.0.

**Return value**

A FluidExchange object.

**Exceptions**

None.

### 25.37.2 setValues(...)

This method modifies the FluidExchange object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FluidExchange](pt01ch25pyo37.md#ker-fluidexchange-fluidexchange-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.37.3 Members

The FluidExchange object has members with the same names and descriptions as the arguments to the [FluidExchange](pt01ch25pyo37.md#ker-fluidexchange-fluidexchange-pyc) method.

### 25.37.4 Corresponding analysis keywords

| [*FLUID EXCHANGE](../key/key-link.md#usb-kws-mfluidexchange) |
| --- |




