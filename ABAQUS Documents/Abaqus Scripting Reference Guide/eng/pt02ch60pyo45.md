# 60.45 Elastic object







The Elastic object specifies elastic material properties.

**Access**

```
materialApi.materials()[*name*].elastic()
```

### 60.45.1 Elastic(...)

This method creates an Elastic object.

**Path**

```
materialApi.materials()[*name*].Elastic
```

**Prototype**

```
odb_Elastic&
Elastic(const odb_SequenceSequenceDouble& table,
        const odb_String& type,
        bool noCompression,
        bool noTension,
        bool temperatureDependency,
        int dependencies,
        const odb_String& moduli);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*type*

An odb_String specifying the type of elasticity data provided. Possible values are:
- "ISOTROPIC"
- "ORTHOTROPIC"
- "ANISOTROPIC"
- "ENGINEERING_CONSTANTS"
- "LAMINA"
- "TRACTION"
- "COUPLED_TRACTION"
- "SHORT_FIBER"
- "SHEAR"

The default value is "ISOTROPIC".

*noCompression*

A Boolean specifying whether compressive stress is allowed. The default value is false.

*noTension*

A Boolean specifying whether tensile stress is allowed. The default value is false.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*moduli*

An odb_String specifying the time-dependence of the elastic material constants. Possible values are "INSTANTANEOUS" and "LONG_TERM". The default value is "LONG_TERM".

**Table data**

If *type*=ISOTROPIC, the table data specify the following:
- The Young's modulus, ![](../graphics/ker_eqn00163.gif).
- The Poisson's ratio, ![](../graphics/ker_eqn00164.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=SHEAR, the table data specify the following:- The shear modulus,![](../graphics/ker_eqn00182.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ENGINEERING_CONSTANTS, the table data specify the following:- ![](../graphics/ker_eqn00183.gif).
- ![](../graphics/ker_eqn00184.gif).
- ![](../graphics/ker_eqn00185.gif).
- ![](../graphics/ker_eqn00186.gif).
- ![](../graphics/ker_eqn00187.gif).
- ![](../graphics/ker_eqn00188.gif).
- ![](../graphics/ker_eqn00189.gif).
- ![](../graphics/ker_eqn00190.gif).
- ![](../graphics/ker_eqn00191.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=LAMINA, the table data specify the following:- ![](../graphics/ker_eqn00183.gif).
- ![](../graphics/ker_eqn00184.gif).
- ![](../graphics/ker_eqn00186.gif).
- ![](../graphics/ker_eqn00189.gif).
- ![](../graphics/ker_eqn00190.gif). This shear modulus is needed to define transverse shear behavior in shells.
- ![](../graphics/ker_eqn00191.gif). This shear modulus is needed to define transverse shear behavior in shells.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ORTHOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00192.gif).
- ![](../graphics/ker_eqn00193.gif).
- ![](../graphics/ker_eqn00194.gif).
- ![](../graphics/ker_eqn00195.gif).
- ![](../graphics/ker_eqn00196.gif).
- ![](../graphics/ker_eqn00197.gif).
- ![](../graphics/ker_eqn00198.gif).
- ![](../graphics/ker_eqn00199.gif).
- ![](../graphics/ker_eqn00200.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ANISOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00192.gif).
- ![](../graphics/ker_eqn00193.gif).
- ![](../graphics/ker_eqn00194.gif).
- ![](../graphics/ker_eqn00195.gif).
- ![](../graphics/ker_eqn00196.gif).
- ![](../graphics/ker_eqn00197.gif).
- ![](../graphics/ker_eqn00201.gif).
- ![](../graphics/ker_eqn00202.gif).
- ![](../graphics/ker_eqn00203.gif).
- ![](../graphics/ker_eqn00198.gif).
- ![](../graphics/ker_eqn00204.gif).
- ![](../graphics/ker_eqn00205.gif).
- ![](../graphics/ker_eqn00206.gif).
- ![](../graphics/ker_eqn00207.gif).
- ![](../graphics/ker_eqn00199.gif).
- ![](../graphics/ker_eqn00208.gif).
- ![](../graphics/ker_eqn00209.gif).
- ![](../graphics/ker_eqn00210.gif).
- ![](../graphics/ker_eqn00211.gif).
- ![](../graphics/ker_eqn00212.gif).
- ![](../graphics/ker_eqn00200.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=TRACTION, the table data specify the following:- ![](../graphics/ker_eqn00163.gif) for warping elements; ![](../graphics/ker_eqn00213.gif) for cohesive elements.
- ![](../graphics/ker_eqn00214.gif) for warping elements; ![](../graphics/ker_eqn00215.gif) for cohesive elements.
- ![](../graphics/ker_eqn00216.gif) for warping elements; ![](../graphics/ker_eqn00217.gif) for cohesive elements.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=COUPLED_TRACTION, the table data specify the following:- ![](../graphics/ker_eqn00213.gif).
- ![](../graphics/ker_eqn00215.gif).
- ![](../graphics/ker_eqn00217.gif).
- ![](../graphics/ker_eqn00218.gif).
- ![](../graphics/ker_eqn00219.gif).
- ![](../graphics/ker_eqn00220.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=SHORT_FIBER, there is no table data.

**Return value**

An Elastic object.

**Exceptions**

RangeError.

### 60.45.2 Members

The Elastic object has members with the same names and descriptions as the arguments to the [Elastic](pt02ch60pyo45.md#ker-elastic-elastic-cpp) method.

In addition, the Elastic object can have the following members:

**Prototype**

```
odb_FailStress failStress() const;
odb_FailStrain failStrain() const;
```

*failStress*

A [FailStress](pt02ch60pyo51.md) object.

*failStrain*

A [FailStrain](pt02ch60pyo50.md) object.

### 60.45.3 Corresponding analysis keywords

| [*ELASTIC](../key/key-link.md#usb-kws-melastic) |
| --- |




