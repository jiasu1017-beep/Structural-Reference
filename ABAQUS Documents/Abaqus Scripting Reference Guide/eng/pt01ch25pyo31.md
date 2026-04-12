# 25.31 FilmCondition object







The FilmCondition object defines film coefficients and associated sink temperatures for coupled temperature-displacement analyses.

The FilmCondition object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.31.1 FilmCondition(...)

This method creates a FilmCondition object.

**Path**

```
mdb.models[*name*].FilmCondition
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the FilmCondition object is created.

*surface*

A [Region](pt01ch45pyo03.md) object specifying the name of the surface to which the film condition interaction is applied.

*definition*

A SymbolicConstant specifying how the film condition is defined. Possible values are EMBEDDED_COEFF, PROPERTY_REF, USER_SUB, and FIELD.

**Optional arguments**

*interactionProperty*

A String specifying the name of the [FilmConditionProp](pt01ch25pyo32.md) object associated with this interaction. The *interactionProperty* argument applies only when *definition*=PROPERTY_REF. The default value is an empty string.

*sinkTemperature*

A Float specifying the reference sink temperature, ![](../graphics/ker_eqn00061.gif). The default value is 0.0.

*sinkAmplitude*

A String specifying the name of the [Amplitude](pt01ch03pyo01.md) object that gives the variation of the sink temperature, ![](../graphics/ker_eqn00061.gif), with time. The default value is an empty string.

**Note:**Use empty string in an Abaqus/Standard analysis to specify that the reference sink temperature is applied immediately at the beginning of the step or linearly over the step. Use empty string in an Abaqus/Explicit analysis to specify that the reference sink temperature is applied throughout the step.

*filmCoeff*

A Float specifying the reference film coefficient value, ![](../graphics/ker_eqn00069.gif). The *filmCoeff* argument applies when *definition*=EMBEDDED_COEFF, *definition*=USER_SUB, or *definition*=FIELD. The default value is 0.0.

*filmCoeffAmplitude*

A String specifying the name of the [Amplitude](pt01ch03pyo01.md) object that gives the variation of the film coefficient, ![](../graphics/ker_eqn00069.gif), with time. The default value is an empty string.

**Note:**Use empty string in an Abaqus/Standard analysis to specify that the reference film coefficient is applied immediately at the beginning of the step or linearly over the step. Use empty string in an Abaqus/Explicit analysis to specify that the reference film coefficient is applied throughout the step.

*field*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) object associated with this interaction. The *field* argument applies only when *definition*=FIELD. The default value is an empty string.

*sinkFieldName*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with the sink temperature. The *sinkFieldName* argument applies only when *sinkDistributionType*=ANALYTICAL_FIELD or *sinkDistributionType*=DISCRETE_FIELD. The default value is an empty string.

*sinkDistributionType*

A SymbolicConstant specifying how the sink temperature is distributed. Possible values are UNIFORM, ANALYTICAL_FIELD, and DISCRETE_FIELD. The default value is UNIFORM.

**Return value**

A FilmCondition object.

**Exceptions**

None.

### 25.31.2 setValues(...)

This method modifies the data for an existing FilmCondition object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FilmCondition](pt01ch25pyo31.md#ker-filmcondition-filmcondition-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.31.3 setValuesInStep(...)

This method modifies the propagating data of an existing FilmCondition object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the interaction is modified.

**Optional arguments**

The optional arguments to `setValuesInStep` are the same as the optional arguments to the [FilmCondition](pt01ch25pyo31.md#ker-filmcondition-filmcondition-pyc) method.
None.

**Return value**

None

**Exceptions**

None.

### 25.31.4 Members

The FilmCondition object has members with the same names and descriptions as the arguments to the [FilmCondition](pt01ch25pyo31.md#ker-filmcondition-filmcondition-pyc) method.




