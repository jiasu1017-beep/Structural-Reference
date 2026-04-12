# 60.42 DruckerPrager object







The DruckerPrager object specifies the extended Drucker-Prager plasticity model.

**Access**

```
materialApi.materials()[*name*].druckerPrager()
```

### 60.42.1 DruckerPrager(...)

This method creates a DruckerPrager object.

**Path**

```
materialApi.materials()[*name*].DruckerPrager
```

**Prototype**

```
odb_DruckerPrager&
DruckerPrager(const odb_SequenceSequenceDouble& table,
              const odb_String& shearCriterion,
              double eccentricity,
              bool testData,
              bool temperatureDependency,
              int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*shearCriterion*

An odb_String specifying the yield criterion. Possible values are "LINEAR", "HYPERBOLIC", and "EXPONENTIAL". The default value is "LINEAR".

This argument applies only to Abaqus/Standard analyses. Only the linear Drucker-Prager model is available in Abaqus/Explicit analyses.

*eccentricity*

A Double specifying the flow potential eccentricity, ![](../graphics/ker_eqn00062.gif), a small positive number that defines the rate at which the hyperbolic flow potential approaches its asymptote. The default value is 0.1.

This argument applies only to Abaqus/Standard analyses.

*testData*

A Boolean specifying whether the material constants for the exponent model are to be computed by Abaqus/Standard from triaxial test data at different levels of confining pressure. The default value is false.

This argument is valid only if *shearCriterion*="EXPONENTIAL".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *shearCriterion*=LINEAR (the only option allowed in an Abaqus/Explicit analysis), the table data specify the following:
- Material angle of friction, ![](../graphics/ker_eqn00095.gif), in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) plane. Give the value in degrees.
- ![](../graphics/ker_eqn00099.gif), the ratio of the flow stress in triaxial tension to the flow stress in triaxial compression. ![](../graphics/ker_eqn00110.gif). If the default value of 0.0 is accepted, a value of 1.0 is assumed.
- Dilation angle, ![](../graphics/ker_eqn00132.gif), in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) plane. Give the value in degrees.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *shearCriterion*=HYPERBOLIC, the table data specify the following:- Material angle of friction, ![](../graphics/ker_eqn00095.gif), at high confining pressure in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) plane. Give the value in degrees.
- Initial hydrostatic tension strength, ![](../graphics/ker_eqn00177.gif).
- Dilation angle, ![](../graphics/ker_eqn00132.gif), at high confining pressure in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) plane. Give the value in degrees.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *shearCriterion*=EXPONENTIAL, the table data specify the following:- Dilation angle, ![](../graphics/ker_eqn00132.gif), at high confining pressure in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) plane. Give the value in degrees.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A DruckerPrager object.

**Exceptions**

RangeError.

### 60.42.2 Members

The DruckerPrager object has members with the same names and descriptions as the arguments to the [DruckerPrager](pt02ch60pyo42.md#ker-druckerprager-druckerprager-cpp) method.

In addition, the DruckerPrager object can have the following members:

**Prototype**

```
odb_DruckerPragerCreep druckerPragerCreep() const;
odb_DruckerPragerHardening druckerPragerHardening() const;
odb_RateDependent rateDependent() const;
odb_TriaxialTestData triaxialTestData() const;
```

*druckerPragerCreep*

A [DruckerPragerCreep](pt02ch60pyo43.md) object.

*druckerPragerHardening*

A [DruckerPragerHardening](pt02ch60pyo44.md) object.

*rateDependent*

A [RateDependent](pt02ch60pyo85.md) object.

*triaxialTestData*

A [TriaxialTestData](pt02ch60pyo99.md) object.

### 60.42.3 Corresponding analysis keywords

| [*DRUCKER PRAGER](../key/key-link.md#usb-kws-mdruckerprager) |
| --- |




