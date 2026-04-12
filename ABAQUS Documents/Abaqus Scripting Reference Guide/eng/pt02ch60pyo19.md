# 60.19 ConcreteCompressionDamage object







The ConcreteCompressionDamage object specifies hardening for the concrete damaged plasticity model.

**Access**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.concreteCompressionDamage()
```

### 60.19.1 ConcreteCompressionDamage(...)

This method creates a ConcreteCompressionDamage object.

**Path**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.ConcreteCompressionDamage
```

**Prototype**

```
odb_ConcreteCompressionDamage&
ConcreteCompressionDamage(const odb_SequenceSequenceDouble& table,
                          double tensionRecovery,
                          bool temperatureDependency,
                          int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*tensionRecovery*

A Double specifying the value of the stiffness recovery factor, ![](../graphics/ker_eqn00127.gif), that determines the amount of tension stiffness that is recovered as loading changes from compression to tension. The default value is 0.0.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Compressive damage variable, ![](../graphics/ker_eqn00128.gif).
- Inelastic (crushing) strain, ![](../graphics/ker_eqn00129.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ConcreteCompressionDamage object.

**Exceptions**

RangeError.

### 60.19.2 Members

The ConcreteCompressionDamage object has members with the same names and descriptions as the arguments to the [ConcreteCompressionDamage](pt02ch60pyo19.md#ker-concretecompressiondamage-concretecompressiondamage-cpp) method.

### 60.19.3 Corresponding analysis keywords

| [*CONCRETE COMPRESSION DAMAGE](../key/key-link.md#usb-kws-mconcretecompdamage) |
| --- |




