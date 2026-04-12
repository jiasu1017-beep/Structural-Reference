# 29.19 ConcreteCompressionDamage object







The ConcreteCompressionDamage object specifies hardening for the concrete damaged plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteCompressionDamage
import odbMaterial
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.concreteCompressionDamage
```

### 29.19.1 ConcreteCompressionDamage(...)

This method creates a ConcreteCompressionDamage object.

**Path**

```
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteCompressionDamage
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity\
.ConcreteCompressionDamage
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*tensionRecovery*

A Float specifying the value of the stiffness recovery factor, ![](../graphics/ker_eqn00127.gif), that determines the amount of tension stiffness that is recovered as loading changes from compression to tension. The default value is 0.0.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

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

### 29.19.2 setValues(...)

This method modifies the ConcreteCompressionDamage object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConcreteCompressionDamage](pt01ch29pyo19.md#ker-concretecompressiondamage-concretecompressiondamage-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.19.3 Members

The ConcreteCompressionDamage object has members with the same names and descriptions as the arguments to the [ConcreteCompressionDamage](pt01ch29pyo19.md#ker-concretecompressiondamage-concretecompressiondamage-pyc) method.

### 29.19.4 Corresponding analysis keywords

| [*CONCRETE COMPRESSION DAMAGE](../key/key-link.md#usb-kws-mconcretecompdamage) |
| --- |




