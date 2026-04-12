# 25.42 GapHeatGeneration object







The GapHeatGeneration object specifies heat generation for a contact interaction property.

**Access**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].heatGeneration
```

### 25.42.1 HeatGeneration(...)

This method creates a GapHeatGeneration object.

**Path**

```
mdb.models[*name*].interactionProperties[*name*].HeatGeneration
```

**Required arguments**

None.

**Optional arguments**

*conversionFraction*

A Float specifying the fraction of dissipated energy caused by friction or electric currents that is converted to heat. The default value is 1.0.

*slaveFraction*

A Float specifying the fraction of converted heat distributed to the slave surface. The default value is 0.5.

**Return value**

A GapHeatGeneration object.

**Exceptions**

None.

### 25.42.2 setValues(...)

This method modifies the GapHeatGeneration object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [GapHeatGeneration](pt01ch25pyo42.md#ker-gapheatgeneration-heatgeneration-pyc) method.

**Return value**

None

**Exceptions**

None.

### 25.42.3 Members

The GapHeatGeneration object has the following members:

*conversionFraction*

A Float specifying the fraction of dissipated energy caused by friction or electric currents that is converted to heat. The default value is 1.0.

*slaveFraction*

A Float specifying the fraction of converted heat distributed to the slave surface. The default value is 0.5.

### 25.42.4 Corresponding analysis keywords

| [*GAP HEAT GENERATION](../key/key-link.md#usb-kws-mgapheatgener) |
| --- |




