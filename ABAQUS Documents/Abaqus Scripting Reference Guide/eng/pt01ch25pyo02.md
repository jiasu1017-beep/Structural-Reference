# 25.2 AcousticImpedance object







The AcousticImpedance object defines surface impedance information or nonreflecting boundaries for acoustic and coupled acoustic-structural analyses.

The AcousticImpedance object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.2.1 AcousticImpedance(...)

This method creates an AcousticImpedance object.

**Path**

```
mdb.models[*name*].AcousticImpedance
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the AcousticImpedance object is created.

*surface*

A [Region](pt01ch45pyo03.md) object specifying the acoustic boundary surface.

**Optional arguments**

*definition*

A SymbolicConstant specifying the type of acoustic impedance to be defined. Possible values are TABULAR and NONREFLECTING. The default value is TABULAR.

*interactionProperty*

A String specifying the [AcousticImpedanceProp](pt01ch25pyo03.md) object associated with this interaction.

*nonreflectingType*

A SymbolicConstant specifying the type of nonreflecting geometry to be defined. Possible values are PLANE, IMPROVED, CIRCULAR, SPHERICAL, ELLIPTICAL, and PROLATE. The default value is PLANE.

This argument is valid only when *definition*=NONREFLECTING.

*radius*

A Float specifying the radius of the circle or sphere defining the boundary surface. The default value is 1.0.

This argument is valid only when *definition*=NONREFLECTING, and *nonreflectingType*=CIRCULAR or SPHERICAL.

*semimajorAxis*

A Float specifying the semimajor axis length of the ellipse or prolate spheroid defining the boundary surface. The default value is 1.0.

This argument is valid only when *definition*=NONREFLECTING, and *nonreflectingType*=ELLIPTICAL or PROLATE.

*eccentricity*

A Float specifying the eccentricity of the ellipse or prolate spheroid defining the boundary surface. The default value is 0.0.

This argument is valid only when *definition*=NONREFLECTING, and *nonreflectingType*=ELLIPTICAL or PROLATE.

*centerCoordinates*

A sequence of three Floats specifying the X, Y, and Z coordinates of the center of the ellipse or prolate spheroid defining the boundary surface. The default value is (0, 0, 0).

This argument is valid only when *definition*=NONREFLECTING, and *nonreflectingType*=ELLIPTICAL or PROLATE.

*directionCosine*

A sequence of three Floats specifying the X, Y, and Z components of the direction cosine of the major axis of the ellipse or prolate spheroid defining the boundary surface. The default value is (0, 0, 1).

This argument is valid only when *definition*=NONREFLECTING, and *nonreflectingType*=ELLIPTICAL or PROLATE.

**Return value**

An AcousticImpedance object.

**Exceptions**

None.

### 25.2.2 setValues(...)

This method modifies the data for an existing AcousticImpedance object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [AcousticImpedance](pt01ch25pyo02.md#ker-acousticimpedance-acousticimpedance-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.2.3 setValuesInStep(...)

This method modifies the propagating data for an existing AcousticImpedance object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the interaction is modified.

**Optional argument**

*interactionProperty*

A String specifying the [AcousticImpedanceProp](pt01ch25pyo03.md) object associated with this interaction.

**Return value**

None

**Exceptions**

None.

### 25.2.4 Members

The AcousticImpedance object has members with the same names and descriptions as the arguments to the [AcousticImpedance](pt01ch25pyo02.md#ker-acousticimpedance-acousticimpedance-pyc) method.

### 25.2.5 Corresponding analysis keywords

| [*SIMPEDANCE](../key/key-link.md#usb-kws-hsimpedance) |
| --- |




