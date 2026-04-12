# 29.94 Sorption object







The Sorption object defines absorption and exsorption behaviors of a partially saturated porous medium in the analysis of coupled wetting liquid flow and porous medium stress.

**Access**

```
import material
mdb.models[*name*].materials[*name*].sorption
import odbMaterial
session.odbs[*name*].materials[*name*].sorption
```

### 29.94.1 Sorption(...)

This method creates a Sorption object.

**Path**

```
mdb.models[*name*].materials[*name*].Sorption
session.odbs[*name*].materials[*name*].Sorption
```

**Required argument**

*absorptionTable*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*lawAbsorption*

A SymbolicConstant specifying absorption behavior. Possible values are LOG and TABULAR. The default value is TABULAR.

*exsorption*

A Boolean specifying whether the exsorption data is specified. The default value is OFF.

*lawExsorption*

A SymbolicConstant specifying exsorption behavior. Possible values are LOG and TABULAR. The default value is TABULAR.

*scanning*

A Float specifying the slope of the scanning line, ![](../graphics/ker_eqn00368.gif). This slope must be positive and larger than the slope of the absorption or exsorption behaviors. The default value is 0.0.

*exsorptionTable*

A sequence of sequences of Floats specifying the items described below. The default value is an empty sequence.

**Table data**

If *lawAbsorption*=TABULAR or *lawExsorption*=TABULAR, the *absorptionTable* and *exsorptionTable* data respectively specify the following: 
- Pore pressure, ![](../graphics/ker_eqn00369.gif).
- Saturation, ![](../graphics/ker_eqn00234.gif).

If *lawAbsorption*=LOG or *lawExsorption*=LOG, the *absorptionTable* and *exsorptionTable* data respectively specify the following: 
- A.
- B.
- ![](../graphics/ker_eqn00370.gif).
- ![](../graphics/ker_eqn00371.gif).

**Return value**

A Sorption object.

**Exceptions**

RangeError.

### 29.94.2 setValues(...)

This method modifies the Sorption object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Sorption](pt01ch29pyo94.md#ker-sorption-sorption-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.94.3 Members

The Sorption object has members with the same names and descriptions as the arguments to the [Sorption](pt01ch29pyo94.md#ker-sorption-sorption-pyc) method.

### 29.94.4 Corresponding analysis keywords

| [*SORPTION](../key/key-link.md#usb-kws-msorption) |
| --- |




