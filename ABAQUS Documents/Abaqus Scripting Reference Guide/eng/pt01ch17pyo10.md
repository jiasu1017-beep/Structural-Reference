# 17.10 InteractionDisplayOptions object







The InteractionDisplayOptions object stores settings that specify how assemblies are to be displayed in a particular viewport when

```
session.viewports[*name*].assemblyDisplay.interactions=ON
```
The InteractionDisplayOptions object has no constructor. When you create a new viewport, the settings are copied from the current viewport.

**Access**

```
session.viewports[*name*].assemblyDisplay.interactionOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.interactionOptions
```

### 17.10.1 setValues(...)

This method modifies the InteractionDisplayOptions object.

**Required arguments**

None.

**Optional arguments**

*surfaceContact*

A Boolean specifying whether surface contact symbols are shown. The default value is ON.

*selfContact*

A Boolean specifying whether self contact symbols are shown. The default value is ON.

*elasticFoundation*

A Boolean specifying whether elastic foundation symbols are shown. The default value is ON.

*actuatorSensor*

A Boolean specifying whether actuator/sensor symbols are shown. The default value is ON.

*radiationAmbient*

A Boolean specifying whether surface radiation-to-ambient symbols are shown. The default value is ON.

*filmCondition*

A Boolean specifying whether surface film condition symbols are shown. The default value is ON.

*concentratedRadiationToAmbient*

A Boolean specifying whether concentrated radiation-to-ambient symbols are shown. The default value is ON.

*concentratedFilmCondition*

A Boolean specifying whether concentrated film condition symbols are shown. The default value is ON.

**Return value**

None

**Exceptions**

RangeError.

### 17.10.2 Members

The InteractionDisplayOptions object has members with the same names and descriptions as the arguments to the [setValues](pt01ch17pyo10.md#ker-interactiondisplayoptions-setvalues-pyc) method.




