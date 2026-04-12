# 17.4 EngineeringFeatureDisplayOptions object







The EngineeringFeatureDisplayOptions object stores settings that specify how assemblies are to be displayed in a particular viewport when

```
session.viewports[*name*].assemblyDisplay.engineeringFeatures=ON
```
The EngineeringFeatureDisplayOptions object has no constructor. When you create a new viewport, the settings are copied from the current viewport.

**Access**

```
session.viewports[*name*].assemblyDisplay.engineeringFeatureOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.engineeringFeatureOptions
import part
session.viewports[*name*].layers[*name*].partDisplay\
.engineeringFeatureOptions
session.viewports[*name*].partDisplay.engineeringFeatureOptions
```

### 17.4.1 setValues(...)

This method modifies the EngineeringFeatureDisplayOptions object.

**Required arguments**

None.

**Optional arguments**

*pointMassInertia*

A Boolean specifying whether point mass inertia symbols are shown. The default value is ON.

*nonstructuralMass*

A Boolean specifying whether nonstructural mass symbols are shown. The default value is ON.

*heatCapacitance*

A Boolean specifying whether heat capacitance symbols are shown. The default value is ON.

*contourIntegral*

A Boolean specifying whether contour integral symbols are shown. The default value is ON.

*springToGround*

A Boolean specifying whether spring-to-ground symbols are shown. The default value is ON.

*twoPointSpring*

A Boolean specifying whether two-point spring symbols are shown. The default value is ON.

**Return value**

None

**Exceptions**

RangeError.

### 17.4.2 Members

The EngineeringFeatureDisplayOptions object has members with the same names and descriptions as the arguments to the [setValues](pt01ch17pyo04.md#ker-engineeringfeaturedisplayoptions-setvalues-pyc) method.




