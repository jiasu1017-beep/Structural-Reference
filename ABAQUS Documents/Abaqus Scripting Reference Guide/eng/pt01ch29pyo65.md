# 29.65 JouleHeatFraction object







The JouleHeatFraction object defines the fraction of electric energy released as heat.

**Access**

```
import material
mdb.models[*name*].materials[*name*].jouleHeatFraction
import odbMaterial
session.odbs[*name*].materials[*name*].jouleHeatFraction
```

### 29.65.1 JouleHeatFraction(...)

This method creates a JouleHeatFraction object.

**Path**

```
mdb.models[*name*].materials[*name*].JouleHeatFraction
session.odbs[*name*].materials[*name*].JouleHeatFraction
```

**Required arguments**

None.

**Optional argument**

*fraction*

A Float specifying the fraction of electrical energy released as heat, including any unit conversion factor. Possible values are 0.0 ![](../graphics/ker_eqn00013.gif) *fraction* ![](../graphics/ker_eqn00013.gif) 1.0. The default value is 1.0.

**Return value**

A JouleHeatFraction object.

**Exceptions**

RangeError.

### 29.65.2 setValues(...)

This method modifies the JouleHeatFraction object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [JouleHeatFraction](pt01ch29pyo65.md#ker-jouleheatfraction-jouleheatfraction-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.65.3 Members

The JouleHeatFraction object has members with the same names and descriptions as the arguments to the [JouleHeatFraction](pt01ch29pyo65.md#ker-jouleheatfraction-jouleheatfraction-pyc) method.

### 29.65.4 Corresponding analysis keywords

| [*JOULE HEAT FRACTION](../key/key-link.md#usb-kws-mjouleheatfrac) |
| --- |




