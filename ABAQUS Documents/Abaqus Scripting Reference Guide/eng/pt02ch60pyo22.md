# 60.22 ConcreteTensionDamage object







The ConcreteTensionDamage object specifies hardening for the concrete damaged plasticity model.

**Access**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.concreteTensionDamage()
```

### 60.22.1 ConcreteTensionDamage(...)

This method creates a ConcreteTensionDamage object.

**Path**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.ConcreteTensionDamage
```

**Prototype**

```
odb_ConcreteTensionDamage&
ConcreteTensionDamage(const odb_SequenceSequenceDouble& table,
                      double compressionRecovery,
                      const odb_String& type,
                      bool temperatureDependency,
                      int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*compressionRecovery*

A Double specifying the value of the stiffness recovery factor, ![](../graphics/ker_eqn00135.gif), that determines the amount of compression stiffness that is recovered as loading changes from tension to compression. The default value is 1.0.

*type*

An odb_String specifying the type of tensile damage data. Set *type*="STRAIN" to specify the tensile damage variable as a function of cracking strain. Set *type*="DISPLACEMENT" to specify the tensile damage variable as a function of cracking displacement. Possible values are "STRAIN" and "DISPLACEMENT". The default value is "STRAIN".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=STRAIN, the table data specify the following:
- Tensile damage variable, ![](../graphics/ker_eqn00136.gif).
- Direct cracking strain, ![](../graphics/ker_eqn00137.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=DISPLACEMENT, the table data specify the following:- Tensile damage variable, ![](../graphics/ker_eqn00136.gif).
- Direct cracking displacement, ![](../graphics/ker_eqn00138.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ConcreteTensionDamage object.

**Exceptions**

RangeError.

### 60.22.2 Members

The ConcreteTensionDamage object has members with the same names and descriptions as the arguments to the [ConcreteTensionDamage](pt02ch60pyo22.md#ker-concretetensiondamage-concretetensiondamage-cpp) method.

### 60.22.3 Corresponding analysis keywords

| [*CONCRETE TENSION DAMAGE](../key/key-link.md#usb-kws-mconcretetensdamage) |
| --- |




