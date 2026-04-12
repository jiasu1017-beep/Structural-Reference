# 60.9 CapCreepConsolidation object







The CapCreepConsolidation object specifies a cap creep model and material properties.

**Access**

```
materialApi.materials()[*name*].capPlasticity().capCreepConsolidation()
```

### 60.9.1 CapCreepConsolidation(...)

This method creates a CapCreepConsolidation object.

**Path**

```
materialApi.materials()[*name*].capPlasticity().CapCreepConsolidation
```

**Prototype**

```
odb_CapCreepConsolidation&
CapCreepConsolidation(const odb_SequenceSequenceDouble& table,
                      const odb_String& law,
                      bool temperatureDependency,
                      int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*law*

An odb_String specifying the cap creep law. Possible values are "STRAIN", "TIME", "SINGHM", and "USER". The default value is "STRAIN".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *law*=STRAIN or *law*=TIME, the table data specify the following:
- ![](../graphics/ker_eqn00010.gif).
- ![](../graphics/ker_eqn00088.gif).
- ![](../graphics/ker_eqn00089.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *law*=SINGHM, the table data specify the following:- ![](../graphics/ker_eqn00010.gif).
- ![](../graphics/ker_eqn00090.gif).
- ![](../graphics/ker_eqn00089.gif).
- ![](../graphics/ker_eqn00091.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CapCreepConsolidation object.

**Exceptions**

None.

### 60.9.2 Members

The CapCreepConsolidation object has members with the same names and descriptions as the arguments to the [CapCreepConsolidation](pt02ch60pyo09.md#ker-capcreepconsolidation-capcreepconsolidation-cpp) method.

### 60.9.3 Corresponding analysis keywords

| [*CAP CREEP](../key/key-link.md#usb-kws-mcapcreep) |
| --- |




