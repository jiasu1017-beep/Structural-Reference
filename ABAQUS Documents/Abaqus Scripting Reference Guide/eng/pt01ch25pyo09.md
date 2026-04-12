# 25.9 CavityRadiationProp object







The CavityRadiationProp object is an interaction property that defines emissivity as a function of temperature and field variables.

The CavityRadiationProp object is derived from the [InteractionProperty](pt01ch25pyo48.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.9.1 CavityRadiationProp(...)

This method creates a CavityRadiationProp object.

**Path**

```
mdb.models[*name*].CavityRadiationProp
```

**Required argument**

*name*

A String specifying the interaction property repository key.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*property*

A sequence of sequences of Floats specifying the following:
- The emissivity, ![](../graphics/ker_eqn00062.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CavityRadiationProp object.

**Exceptions**

None.

### 25.9.2 setValues(...)

This method modifies the CavityRadiationProp object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CavityRadiationProp](pt01ch25pyo09.md#ker-cavityradiationprop-cavityradiationprop-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 25.9.3 Members

The CavityRadiationProp object has members with the same names and descriptions as the arguments to the [CavityRadiationProp](pt01ch25pyo09.md#ker-cavityradiationprop-cavityradiationprop-pyc) method.

### 25.9.4 Corresponding analysis keywords

| [*EMISSIVITY](../key/key-link.md#usb-kws-memissivity) |
| --- |




