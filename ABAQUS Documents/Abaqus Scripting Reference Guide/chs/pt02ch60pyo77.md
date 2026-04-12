# 60.77 Plastic object







The Plastic object specifies a metal plasticity model.

**Access**

```
materialApi.materials()[*name*].plastic()
```

### 60.77.1 Plastic(...)

This method creates a Plastic object.

**Path**

```
materialApi.materials()[*name*].Plastic
```

**Prototype**

```
odb_Plastic&
Plastic(const odb_SequenceSequenceDouble& table,
        const odb_String& hardening,
        bool rate,
        const odb_String& dataType,
        bool strainRangeDependency,
        int numBackstresses,
        bool temperatureDependency,
        int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*hardening*

An odb_String specifying the type of hardening. Possible values are "ISOTROPIC", "KINEMATIC", "COMBINED", "JOHNSON_COOK", and "USER". The default value is "ISOTROPIC".

*rate*

A Boolean specifying whether the data depend on rate. The default value is false.

*dataType*

An odb_String specifying the type of combined hardening. This argument is only valid if *hardening*="COMBINED". Possible values are "HALF_CYCLE", "PARAMETERS", and "STABILIZED". The default value is "HALF_CYCLE".

*strainRangeDependency*

A Boolean specifying whether the data depend on strain range. This argument is only valid if *hardening*="COMBINED" and *dataType*="STABILIZED". The default value is false.

*numBackstresses*

An Int specifying the number of backstresses. This argument is only valid if *hardening*="COMBINED".                 The default value is 1.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *hardening*=ISOTROPIC, or if *hardening*=COMBINED and *dataType*=HALF_CYCLE, the table data specify the following:
- Yield stress.
- Plastic strain.
- Equivalent plastic strain rate, ![](../graphics/ker_eqn00337.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *hardening*=COMBINED and *dataType*=STABILIZED, the table data specify the following:- Yield stress.
- Plastic strain.
- Strain range, if the data depend on strain range.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *hardening*=COMBINED and *dataType*=PARAMETERS, the table data specify the following:- Yield stress at zero plastic strain.
- The first kinematic hardening parameter, ![](../graphics/ker_eqn00338.gif).
- The first kinematic hardening parameter, ![](../graphics/ker_eqn00339.gif).
- If applicable, the second kinematic hardening parameter, ![](../graphics/ker_eqn00340.gif).
- If applicable, the second kinematic hardening parameter, ![](../graphics/ker_eqn00341.gif).
- Etc.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *hardening*=KINEMATIC, the table data specify the following:- Yield stress.
- Plastic strain.
- Temperature, if the data depend on temperature.

If *hardening*=JOHNSON_COOK, the table data specify the following:- A.
- B.
- n.
- m.
- Melting temperature.
- Transition temperature.

If *hardening*=USER, the table data specify the following:- Hardening properties.

**Return value**

A Plastic object.

**Exceptions**

RangeError.

### 60.77.2 Members

The Plastic object has members with the same names and descriptions as the arguments to the [Plastic](pt02ch60pyo77.md#ker-plastic-plastic-cpp) method.

In addition, the Plastic object can have the following members:

**Prototype**

```
odb_RateDependent rateDependent() const;
odb_Potential potential() const;
odb_CyclicHardening cyclicHardening() const;
odb_Ornl ornl() const;
odb_CycledPlastic cycledPlastic() const;
odb_AnnealTemperature annealTemperature() const;
```

*rateDependent*

A [RateDependent](pt02ch60pyo85.md) object.

*potential*

A [Potential](pt02ch60pyo83.md) object.

*cyclicHardening*

A [CyclicHardening](pt02ch60pyo30.md) object.

*ornl*

An [Ornl](pt02ch60pyo73.md) object.

*cycledPlastic*

A [CycledPlastic](pt02ch60pyo29.md) object.

*annealTemperature*

An [AnnealTemperature](pt02ch60pyo03.md) object.

### 60.77.3 Corresponding analysis keywords

| [*PLASTIC](../key/key-link.md#usb-kws-mplastic) |
| --- |




