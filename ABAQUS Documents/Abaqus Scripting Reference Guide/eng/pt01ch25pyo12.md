# 25.12 ConcentratedFilmCondition object







The ConcentratedFilmCondition object defines concentrated film coefficients and associated sink temperatures.

The ConcentratedFilmCondition object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.12.1 ConcentratedFilmCondition(...)

This method creates a ConcentratedFilmCondition object.

**Path**

```
mdb.models[*name*].ConcentratedFilmCondition
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the ConcentratedFilmCondition object is created.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the concentrated film condition interaction is applied. The interaction is applied to each node in the region.

*definition*

A SymbolicConstant specifying how the concentrated film condition is defined. Possible values are EMBEDDED_COEFF, PROPERTY_REF, USER_SUB, and FIELD.

**Optional arguments**

*nodalArea*

A Float specifying the area associated with the node where the concentrated film condition is applied. The default value is 1.0.

*explicitRegionType*

A SymbolicConstant specifying how the concentrated film condition is applied to the boundary of an adaptive mesh domain. Possible values are LAGRANGIAN, SLIDING, and EULERIAN. The default value is LAGRANGIAN.

This argument applies only during an Abaqus/Explicit analysis.

*interactionProperty*

A String specifying the name of the [FilmConditionProp](pt01ch25pyo32.md) object associated with this interaction. The *interactionProperty* argument applies only when *definition*=PROPERTY_REF. The default value is an empty string.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this interaction. The *field* argument applies only when *definition*=FIELD. The default value is an empty string.

*sinkTemperature*

A Float specifying the reference sink temperature, ![](../graphics/ker_eqn00061.gif). The default value is 0.0.

*sinkAmplitude*

A String specifying the name of the [Amplitude](pt01ch03pyo01.md) object that gives the variation of the sink temperature, ![](../graphics/ker_eqn00061.gif), with time. The default value is an empty string.

**Note:**Use `None` in an Abaqus/Standard analysis to specify that the reference sink temperature is applied immediately at the beginning of the step or linearly over the step. Use `None` in an Abaqus/Explicit analysis to specify that the reference sink temperature is applied throughout the step.

*filmCoeff*

A Float specifying the reference film coefficient value, ![](../graphics/ker_eqn00069.gif). The *filmCoeff* argument applies when *definition*=EMBEDDED_COEFF, *definition*=USER_SUB, or *definition*=FIELD. The default value is 0.0.

*filmCoeffAmplitude*

A String specifying the name of the [Amplitude](pt01ch03pyo01.md) object that gives the variation of the film coefficient, ![](../graphics/ker_eqn00069.gif), with time. The default value is an empty string.

**Note:**Use `None` in an Abaqus/Standard analysis to specify that the reference film coefficient is applied immediately at the beginning of the step or linearly over the step. Use `None` in an Abaqus/Explicit analysis to specify that the reference film coefficient is applied throughout the step.

*sinkFieldName*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with the sink temperature. The *sinkFieldName* argument applies only when *sinkDistributionType*=ANALYTICAL_FIELD or *sinkDistributionType*=DISCRETE_FIELD. The default value is an empty string.

*sinkDistributionType*

A SymbolicConstant specifying how the sink temperature is distributed. Possible values are UNIFORM, ANALYTICAL_FIELD, and DISCRETE_FIELD. The default value is UNIFORM.

**Return value**

A ConcentratedFilmCondition object.

**Exceptions**

None.

### 25.12.2 setValues(...)

This method modifies the data for an existing ConcentratedFilmCondition object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConcentratedFilmCondition](pt01ch25pyo12.md#ker-concentratedfilmcondition-concentratedfilmcondition-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.12.3 setValuesInStep(...)

This method modifies the propagating data of an existing ConcentratedFilmCondition object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the interaction is modified.

**Optional arguments**

The optional arguments to `setValuesInStep` are the same as the optional arguments to the [ConcentratedFilmCondition](pt01ch25pyo12.md#ker-concentratedfilmcondition-concentratedfilmcondition-pyc) method, except for the *explicitRegionType* argument.
None.

**Return value**

None

**Exceptions**

None.

### 25.12.4 Members

The ConcentratedFilmCondition object has members with the same names and descriptions as the arguments to the [ConcentratedFilmCondition](pt01ch25pyo12.md#ker-concentratedfilmcondition-concentratedfilmcondition-pyc) method.




