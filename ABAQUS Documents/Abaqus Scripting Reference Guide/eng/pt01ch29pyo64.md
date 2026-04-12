# 29.64 InelasticHeatFraction object







The InelasticHeatFraction object defines the fraction of the rate of inelastic dissipation that appears as a heat source.

**Access**

```
import material
mdb.models[*name*].materials[*name*].inelasticHeatFraction
import odbMaterial
session.odbs[*name*].materials[*name*].inelasticHeatFraction
```

### 29.64.1 InelasticHeatFraction(...)

This method creates an InelasticHeatFraction object.

**Path**

```
mdb.models[*name*].materials[*name*].InelasticHeatFraction
session.odbs[*name*].materials[*name*].InelasticHeatFraction
```

**Required arguments**

None.

**Optional argument**

*fraction*

A Float specifying the fraction of inelastic dissipation rate that appears as a heat flux per unit volume. The fraction may include a unit conversion factor if required. Possible values are 0.0 ![](../graphics/ker_eqn00013.gif) *fraction* ![](../graphics/ker_eqn00013.gif) 1.0. The default value is 0.9.

**Return value**

An InelasticHeatFraction object.

**Exceptions**

RangeError.

### 29.64.2 setValues(...)

This method modifies the InelasticHeatFraction object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [InelasticHeatFraction](pt01ch29pyo64.md#ker-inelasticheatfraction-inelasticheatfraction-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.64.3 Members

The InelasticHeatFraction object has members with the same names and descriptions as the arguments to the [InelasticHeatFraction](pt01ch29pyo64.md#ker-inelasticheatfraction-inelasticheatfraction-pyc) method.

### 29.64.4 Corresponding analysis keywords

| [*INELASTIC HEAT FRACTION](../key/key-link.md#usb-kws-minelastheatfrac) |
| --- |




