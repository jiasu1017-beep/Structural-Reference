# 25.44 IncidentWave object







The IncidentWave object defines incident wave interactions for acoustic and coupled acoustic-structural analyses.

The IncidentWave object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.44.1 IncidentWave(...)

This method creates an IncidentWave object.

**Path**

```
mdb.models[*name*].IncidentWave
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the IncidentWave object is created.

*sourcePoint*

A [Region](pt01ch45pyo03.md) object specifying the incident wave source point.

*standoffPoint*

A [Region](pt01ch45pyo03.md) object specifying the incident wave standoff point.

This argument is not valid when *definition*=CONWEP.

*surface*

A [Region](pt01ch45pyo03.md) object specifying the surface defining the incident wave interaction.  In problems involving fluid/surface boundaries, both the fluid surface and the solid surface comprising the boundary must have an incident wave interaction specified.

*interactionProperty*

A String specifying the [IncidentWaveProperty](pt01ch25pyo45.md) object associated with this interaction.

**Optional arguments**

*definition*

A SymbolicConstant specifying the type of incident wave to be defined. The value must be PRESSURE for linear perturbation steps. An Explicit step is required when the value is set to CONWEP. Possible values are PRESSURE, ACCELERATION, UNDEX, and CONWEP. The default value is PRESSURE.

*amplitude*

A String specifying the name of the [Amplitude](pt01ch03pyo01.md) object that defines the fluid pressure time history at the standoff point, if *definition*=PRESSURE.  If *definition*=ACCELERATION, then this string specifies the name of the [Amplitude](pt01ch03pyo01.md) object that defines the fluid particle acceleration time history at the standoff point. This member can be specified only if *definition*=PRESSURE or ACCELERATION. The default value is an empty string.

*imaginaryAmplitude*

A String specifying the name of the [Amplitude](pt01ch03pyo01.md) object that defines the imaginary component of the fluid pressure time history at the standoff point.  This member is applicable only for linear perturbation steps and if *definition*=PRESSURE. The default value is an empty string.

*surfaceNormal*

A sequence of three Floats specifying the X, Y, and Z components of the direction cosine of the fluid surface normal.

This argument is valid only when *definition*=UNDEX.

*initialDepth*

 `None` or a Float specifying the initial depth of the UNDEX bubble. The default value is `None`.

This argument is valid only when *definition*=UNDEX.

*referenceMagnitude*

A Float specifying the reference magnitude.

This argument is not valid when *definition*=CONWEP.

*detonationTime*

A Float specifying the time of detonation, given in total time.

This argument is valid only when *definition*=CONWEP.

*magnitudeFactor*

A Float specifying the magnitude scale factor. The default value is 1.0.

This argument is valid only when *definition*=CONWEP.

**Return value**

An IncidentWave object.

**Exceptions**

None.

### 25.44.2 setValues(...)

This method modifies the IncidentWave object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [IncidentWave](pt01ch25pyo44.md#ker-incidentwave-incidentwave-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.44.3 Members

The IncidentWave object has members with the same names and descriptions as the arguments to the [IncidentWave](pt01ch25pyo44.md#ker-incidentwave-incidentwave-pyc) method.

### 25.44.4 Corresponding analysis keywords

| [*INCIDENT WAVE INTERACTION](../key/key-link.md#usb-kws-hincidentwaveinteraction) |
| --- |




