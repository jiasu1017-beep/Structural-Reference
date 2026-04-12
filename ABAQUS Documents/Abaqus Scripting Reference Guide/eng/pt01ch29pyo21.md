# 29.21 ConcreteDamagedPlasticity object







The ConcreteDamagedPlasticity object specifies the concrete damaged plasticity model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].concreteDamagedPlasticity
import odbMaterial
session.odbs[*name*].materials[*name*].concreteDamagedPlasticity
```

### 29.21.1 ConcreteDamagedPlasticity(...)

This method creates a ConcreteDamagedPlasticity object.

**Path**

```
mdb.models[*name*].materials[*name*].ConcreteDamagedPlasticity
session.odbs[*name*].materials[*name*].ConcreteDamagedPlasticity
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

The table data specify the following:
- Dilation angle, ![](../graphics/ker_eqn00132.gif) (in degrees) in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) plane.
- Flow potential eccentricity, ![](../graphics/ker_eqn00062.gif). The default value is 0.1.
- ![](../graphics/ker_eqn00133.gif), the ratio of initial equibiaxial compressive yield stress to initial uniaxial compressive yield stress. The default value is 1.16.
- ![](../graphics/ker_eqn00134.gif), the ratio of the second stress invariant on the tensile meridian, to that on the compressive meridian, at initial yield for any given value of the pressure invariant ![](../graphics/ker_eqn00092.gif) such that the maximum principal stress is negative. The default value is 2/3.
- Viscosity parameter, ![](../graphics/ker_eqn00041.gif), used for the viscoplastic regularization of the concrete constitutive equations in an Abaqus/Standard analysis. This parameter is ignored in an Abaqus/Explicit analysis. The default value is 0.0.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ConcreteDamagedPlasticity object.

**Exceptions**

RangeError.

### 29.21.2 setValues(...)

This method modifies the ConcreteDamagedPlasticity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConcreteDamagedPlasticity](pt01ch29pyo21.md#ker-concretedamagedplasticity-concretedamagedplasticity-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.21.3 Members

The ConcreteDamagedPlasticity object has members with the same names and descriptions as the arguments to the [ConcreteDamagedPlasticity](pt01ch29pyo21.md#ker-concretedamagedplasticity-concretedamagedplasticity-pyc) method.

In addition, the ConcreteDamagedPlasticity object can have the following members:

*concreteCompressionHardening*

A [ConcreteCompressionHardening](pt01ch29pyo20.md) object.

*concreteTensionStiffening*

A [ConcreteTensionStiffening](pt01ch29pyo23.md) object.

*concreteCompressionDamage*

A [ConcreteCompressionDamage](pt01ch29pyo19.md) object.

*concreteTensionDamage*

A [ConcreteTensionDamage](pt01ch29pyo22.md) object.

### 29.21.4 Corresponding analysis keywords

| [*CONCRETE DAMAGED PLASTICITY](../key/key-link.md#usb-kws-mconcretedamagedplast) |
| --- |




