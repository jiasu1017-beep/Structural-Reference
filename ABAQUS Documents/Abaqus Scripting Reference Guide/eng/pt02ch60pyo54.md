# 60.54 GapFlow object







The GapFlow object specifies tangential flow constitutive parameters for pore pressure cohesive elements.

**Access**

```
materialApi.materials()[*name*].gapFlow()
```

### 60.54.1 GapFlow(...)

This method creates an GapFlow object.

**Path**

```
materialApi.materials()[*name*].GapFlow
```

**Prototype**

```
odb_GapFlow&
GapFlow(const odb_SequenceSequenceDouble& table,
        odb_Union kmax,
        bool temperatureDependency,
        int dependencies,
        const odb_String& type);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*kmax*

The string "NONE" or a Double specifying the maximum permeability value that should be used. If *kmax*="NONE", Abaqus assumes that the permeability is not bounded. This value is meaningful only when *type*="NEWTONIAN". The default value is "NONE".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*type*

An odb_String specifying the type of gap flow. Possible values are "NEWTONIAN" and "POWER_LAW". The default value is "NEWTONIAN".

**Table data**

If *type*=NEWTONIAN the table data specify the following:
- Pore viscosity.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=POWER_LAW the table data specify the following:- Consistency.
- Exponent.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A GapFlow object.

**Exceptions**

None.

### 60.54.2 Members

The GapFlow object has members with the same names and descriptions as the arguments to the [GapFlow](pt02ch60pyo54.md#ker-gapflow-gapflow-cpp) method.

### 60.54.3 Corresponding analysis keywords

| [*GAP FLOW](../key/key-link.md#usb-kws-mgapflow) |
| --- |




