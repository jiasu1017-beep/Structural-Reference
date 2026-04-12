# 25.21 ContactProperty object







The ContactProperty object defines a contact interaction property.

The ContactProperty object is derived from the [InteractionProperty](pt01ch25pyo48.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.21.1 ContactProperty(...)

This method creates a ContactProperty object.

**Path**

```
mdb.models[*name*].ContactProperty
```

**Required argument**

*name*

A String specifying the interaction property repository key.

**Optional arguments**

None.

**Return value**

A ContactProperty object.

**Exceptions**

None.

### 25.21.2 Members

The ContactProperty object can have the following members:

*tangentialBehavior*

A [ContactTangentialBehavior](pt01ch25pyo25.md) object.

*normalBehavior*

A [NormalBehavior](pt01ch25pyo53.md) object.

*damping*

A [ContactDamping](pt01ch25pyo18.md) object.

*damage*

A [ContactDamage](pt01ch25pyo17.md) object.

*fractureCriterion*

A [FractureCriterion](pt01ch25pyo40.md) object.

*cohesiveBehavior*

A [CohesiveBehavior](pt01ch25pyo11.md) object.

*thermalConductance*

A [ThermalConductance](pt01ch25pyo78.md) object.

*heatGeneration*

A [GapHeatGeneration](pt01ch25pyo42.md) object.

*radiation*

A [Radiation](pt01ch25pyo56.md) object.

*geometricProperties*

A [GeometricProperties](pt01ch25pyo43.md) object.

*electricalConductance*

A [GapElectricalConductance](pt01ch25pyo41.md) object.

### 25.21.3 Corresponding analysis keywords

| [*SURFACE INTERACTION](../key/key-link.md#usb-kws-hsurfaceinteraction) |
| --- |




