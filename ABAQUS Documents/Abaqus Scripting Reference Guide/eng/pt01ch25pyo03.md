# 25.3 AcousticImpedanceProp object







The AcousticImpedanceProp object is an interaction property that defines the properties referred to by an [AcousticImpedance](pt01ch25pyo02.md) object.

The AcousticImpedanceProp object is derived from the [InteractionProperty](pt01ch25pyo48.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.3.1 AcousticImpedanceProp(...)

This method creates an AcousticImpedanceProp object.

**Path**

```
mdb.models[*name*].AcousticImpedanceProp
```

**Required arguments**

*name*

A String specifying the interaction property repository key.

*tableType*

A SymbolicConstant specifying the type of tabular data to be defined. Possible values are IMPEDANCE and ADMITTANCE.

*table*

A sequence of sequences of Floats specifying acoustic impedance properties.

If *tableType*=IMPEDANCE, each sequence of the table data specifies: 
- The real part of the complex impedance.
- The imaginary part of the complex impedance.
- Frequency, if the data depend on frequency.

If *tableType*=ADMITTANCE, each sequence of the table data specifies: 
- The real part of the complex admittance.
- The imaginary part of the complex admittance.
- Frequency, if the data depend on frequency.

**Optional argument**

*frequencyDependency*

A Boolean specifying whether the *table* data depend on frequency. The default value is OFF.

**Return value**

An AcousticImpedanceProp object.

**Exceptions**

None.

### 25.3.2 setValues(...)

This method modifies the AcousticImpedanceProp object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [AcousticImpedanceProp](pt01ch25pyo03.md#ker-acousticimpedanceprop-acousticimpedanceprop-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 25.3.3 Members

The AcousticImpedanceProp object has members with the same names and descriptions as the arguments to the [AcousticImpedanceProp](pt01ch25pyo03.md#ker-acousticimpedanceprop-acousticimpedanceprop-pyc) method.

### 25.3.4 Corresponding analysis keywords

| [*IMPEDANCE PROPERTY](../key/key-link.md#usb-kws-mimpedanceprop) |
| --- |




