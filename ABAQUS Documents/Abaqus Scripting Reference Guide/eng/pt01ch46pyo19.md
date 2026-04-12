# 46.19 RebarLayers object







The RebarLayers object defines the rebar properties of a section.

**Access**

```
import section
mdb.models[*name*].parts[*name*].compositeLayups[*i*].section.rebarLayers
mdb.models[*name*].sections[*name*].rebarLayers
import odbSection
session.odbs[*name*].sections[*name*].rebarLayers
```

### 46.19.1 RebarLayers(...)

This method creates a RebarLayers object.

**Path**

```
mdb.models[*name*].parts[*name*].compositeLayups[*i*].section.RebarLayers
mdb.models[*name*].sections[*name*].RebarLayers
session.odbs[*name*].sections[*name*].RebarLayers
```

**Required arguments**

*rebarSpacing*

A SymbolicConstant specifying the type of rebar geometry. Possible values are CONSTANT, ANGULAR, and LIFT_EQUATION.

*layerTable*

A [LayerPropertiesArray](pt01ch46pyo15.md) object specifying the layers of reinforcement.

**Optional arguments**

None.

**Return value**

A RebarLayers object.

**Exceptions**

None.

### 46.19.2 setValues(...)

This method modifies the RebarLayers object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [RebarLayers](pt01ch46pyo19.md#ker-rebarlayers-rebarlayers-pyc) method.

**Return value**

None

**Exceptions**

None.

### 46.19.3 Members

The RebarLayers object has members with the same names and descriptions as the arguments to the [RebarLayers](pt01ch46pyo19.md#ker-rebarlayers-rebarlayers-pyc) method.

### 46.19.4 Corresponding analysis keywords

| [*REBAR LAYER](../key/key-link.md#usb-kws-mrebarlayer) |
| --- |




