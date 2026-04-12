# 25.14 ConcentratedRadiationToAmbient object







The ConcentratedRadiationToAmbient object defines radiant heat transfer between a point and its nonreflecting environment.

The ConcentratedRadiationToAmbient object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.14.1 ConcentratedRadiationToAmbient(...)

This method creates a ConcentratedRadiationToAmbient object.

**Path**

```
mdb.models[*name*].ConcentratedRadiationToAmbient
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the ConcentratedRadiationToAmbient object is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the concentrated radiation interaction is applied. The interaction is applied to each node in the region.

*ambientTemperature*

A Float specifying the reference ambient temperature, ![](../graphics/ker_eqn00061.gif).

*ambientTemperatureAmp*

A String specifying the name of the [Amplitude](pt01ch03pyo01.md) object that gives the variation of the ambient temperature with time. 

**Note:**Use `None` in an Abaqus/Standard analysis to specify that the reference ambient temperature is applied immediately at the beginning of the step or linearly over the step. Use `None` in an Abaqus/Explicit analysis to specify that the reference ambient temperature is applied throughout the step.

*emissivity*

A Float specifying the emissivity, ![](../graphics/ker_eqn00062.gif).

**Optional arguments**

*nodalArea*

A Float specifying the area associated with the node where the concentrated radiation interaction is applied. The default value is 1.0.

*explicitRegionType*

A SymbolicConstant specifying how the concentrated radiation is applied to the boundary of an adaptive mesh domain. Possible values are LAGRANGIAN, SLIDING, and EULERIAN. The default value is LAGRANGIAN.

**Note:** *explicitRegionType* applies only during an Abaqus/Explicit analysis.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this interaction. The *field* argument applies only when *distributionType*=ANALYTICAL_FIELD. The default value is an empty string.

*distributionType*

A SymbolicConstant specifying how the radiation is defined. Possible values are UNIFORM and ANALYTICAL_FIELD. The default value is UNIFORM.

**Return value**

A ConcentratedRadiationToAmbient object.

**Exceptions**

None.

### 25.14.2 setValues(...)

This method modifies the data for an existing ConcentratedRadiationToAmbient object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConcentratedRadiationToAmbient](pt01ch25pyo14.md#ker-concentratedradiationtoambient-concentratedradiation-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.14.3 setValuesInStep(...)

This method modifies the propagating data of an existing ConcentratedRadiationToAmbient object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the interaction is modified.

**Optional arguments**

The optional arguments to `setValuesInStep` are the same as the arguments to the [ConcentratedRadiationToAmbient](pt01ch25pyo14.md#ker-concentratedradiationtoambient-concentratedradiation-pyc) method, except for the *name*, *createStepName*, *region*, and *explicitRegionType* arguments.
None.

**Return value**

None

**Exceptions**

None.

### 25.14.4 Members

The ConcentratedRadiationToAmbient object has members with the same names and descriptions as the arguments to the [ConcentratedRadiationToAmbient](pt01ch25pyo14.md#ker-concentratedradiationtoambient-concentratedradiation-pyc) method.




