# 29.20 ConcreteCompressionHardening object







The ConcreteCompressionHardening object specifies hardening for the concrete damaged plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteCompressionHardening
import odbMaterial
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteCompressionHardening
```

### 29.20.1 ConcreteCompressionHardening(...)

This method creates a ConcreteCompressionHardening object.

**Path**

```
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteCompressionHardening
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteCompressionHardening
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*rate*

A Boolean specifying whether the data depend on rate. The default value is OFF.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

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

### 29.20.2 setValues(...)

This method modifies the ConcreteCompressionHardening object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConcreteCompressionHardening](pt01ch29pyo20.md#ker-concretecompressionhardening-concretecompressionhard-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.20.3 Members

The ConcreteCompressionHardening object has members with the same names and descriptions as the arguments to the [ConcreteCompressionHardening](pt01ch29pyo20.md#ker-concretecompressionhardening-concretecompressionhard-pyc) method.

### 29.20.4 Corresponding analysis keywords

| [*CONCRETE COMPRESSION HARDENING](../key/key-link.md#usb-kws-mconcretecomphard) |
| --- |




