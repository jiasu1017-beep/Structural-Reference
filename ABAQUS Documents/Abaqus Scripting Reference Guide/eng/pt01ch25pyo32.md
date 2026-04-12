# 25.32 FilmConditionProp object







The FilmConditionProp object is an interaction property that defines a film coefficient as a function of temperature and field variables.

The FilmConditionProp object is derived from the [InteractionProperty](pt01ch25pyo48.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.32.1 FilmConditionProp(...)

This method creates a FilmConditionProp object.

**Path**

```
mdb.models[*name*].FilmConditionProp
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
- The film coefficient, ![](../graphics/ker_eqn00069.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A FilmConditionProp object.

**Exceptions**

None.

### 25.32.2 setValues(...)

This method modifies the FilmConditionProp object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FilmConditionProp](pt01ch25pyo32.md#ker-filmconditionprop-filmconditionprop-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 25.32.3 Members

The FilmConditionProp object has members with the same names and descriptions as the arguments to the [FilmConditionProp](pt01ch25pyo32.md#ker-filmconditionprop-filmconditionprop-pyc) method.

### 25.32.4 Corresponding analysis keywords

| [*FILM PROPERTY](../key/key-link.md#usb-kws-mfilmproperty) |
| --- |




