# 51.7 Monitor object







The Monitor object defines a degree of freedom to monitor.

**Access**

```
import step
mdb.models[*name*].steps[*name*].monitor
```

### 51.7.1 Monitor(...)

This method creates a request for a degree of freedom to be monitored in a general or modal procedure.

**Path**

```
mdb.models[*name*].steps[*name*].Monitor
```

**Required arguments**

*node*

A String specifying the name of the region to be monitored.

*dof*

A SymbolicConstant specifying the degree of freedom to be monitored at the node. Possible values are:
- U1
- U2
- U3
- UR1
- UR2
- UR3
- WARP
- FLUID_PRESSURE
- ELECTRICAL_POTENTIAL
- NT11
- NT30
- NN11
- NN30

The NT identifiers are not available for mass diffusion. The NN identifiers are available only for mass diffusion.

*frequency*

An Int specifying the output frequency in increments. This argument is valid only for an Abaqus/Standard analysis.

**Optional arguments**

None.

**Return value**

A Monitor object.

**Exceptions**

RangeError.

### 51.7.2 setValues(...)

This method modifies the Monitor object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Monitor](pt01ch51pyo07.md#ker-monitor-monitor-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 51.7.3 Members

The Monitor object has members with the same names and descriptions as the arguments to the [Monitor](pt01ch51pyo07.md#ker-monitor-monitor-pyc) method.

### 51.7.4 Corresponding analysis keywords

| [*MONITOR](../key/key-link.md#usb-kws-hmonitor) |
| --- |




