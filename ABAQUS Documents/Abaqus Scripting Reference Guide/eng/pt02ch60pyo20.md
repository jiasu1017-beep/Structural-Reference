# 60.20 ConcreteCompressionHardening object







The ConcreteCompressionHardening object specifies hardening for the concrete damaged plasticity model.

**Access**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.concreteCompressionHardening()
```

### 60.20.1 ConcreteCompressionHardening(...)

This method creates a ConcreteCompressionHardening object.

**Path**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.ConcreteCompressionHardening
```

**Prototype**

```
odb_ConcreteCompressionHardening&
ConcreteCompressionHardening(const odb_SequenceSequenceDouble& table,
                             bool rate,
                             bool temperatureDependency,
                             int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*rate*

A Boolean specifying whether the data depend on rate. The default value is false.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Yield stress in compression, ![](../graphics/ker_eqn00102.gif).
- Inelastic (crushing) strain, ![](../graphics/ker_eqn00130.gif).
- Inelastic (crushing) strain rate, ![](../graphics/ker_eqn00131.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ConcreteCompressionHardening object.

**Exceptions**

RangeError.

### 60.20.2 Members

The ConcreteCompressionHardening object has members with the same names and descriptions as the arguments to the [ConcreteCompressionHardening](pt02ch60pyo20.md#ker-concretecompressionhardening-concretecompressionhard-cpp) method.

### 60.20.3 Corresponding analysis keywords

| [*CONCRETE COMPRESSION HARDENING](../key/key-link.md#usb-kws-mconcretecomphard) |
| --- |




