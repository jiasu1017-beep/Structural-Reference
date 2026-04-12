# 63.8 ConnectorSection object







A ConnectorSection object describes the connection type and the behavior of a connector.

The ConnectorSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.8.1 ConnectorSection(...)

This method creates a ConnectorSection object.

**Path**

```
sectionApi.ConnectorSection
```

**Prototype**

```
odb_ConnectorSection&
ConnectorSection(const odb_String& name,
  const odb_String& assembledType,
  const odb_String& rotationalType,
  const odb_String& translationalType,
  const odb_String& integration,
  odb_Union u1ReferenceLength,
  odb_Union u2ReferenceLength,
  odb_Union u3ReferenceLength,
  odb_Union ur1ReferenceAngle,
  odb_Union ur2ReferenceAngle,
  odb_Union ur3ReferenceAngle,
  odb_Union massPerLength,
  odb_Union contactAngle,
  double materialFlowFactor,
  bool regularize,
  bool defaultTolerance,
  double regularization,
  const odb_String& extrapolation,
  const odb_SequenceConnectorBehaviorOption& behaviorOptions);
```

**Required argument**

*name*

An odb_String specifying the repository key.

**Optional arguments**

*assembledType*

An odb_String specifying the assembled connection type. Possible values are:
- "NONE"
- "BEAM"
- "BUSHING"
- "CVJOINT"
- "CYLINDRICAL"
- "HINGE"
- "PLANAR"
- "RETRACTOR"
- "SLIPRING"
- "TRANSLATOR"
- "UJOINT"
- "WELD"

The default value is "NONE".

You cannot include the *assembledType* argument if *translationalType* or *rotationalType* are given a value other than "NONE". At least one of the arguments *assembledType*, *translationalType*, or *rotationalType* must be given a value other than "NONE".

*rotationalType*

An odb_String specifying the basic rotational connection type. Possible values are:
- "NONE"
- "ALIGN"
- "CARDAN"
- "CONSTANT_VELOCITY"
- "EULER"
- "FLEXION_TORSION"
- "FLOW_CONVERTER"
- "PROJECTION_FLEXION_TORSION"
- "REVOLUTE"
- "ROTATION"
- "ROTATION_ACCELEROMETER"
- "UNIVERSAL"

The default value is "NONE".

You cannot include the *rotationalType* argument if *assembledType* is given a value other than "NONE". At least one of the arguments *assembledType*, *translationalType*, or *rotationalType* must be given an value other than "NONE".

*translationalType*

An odb_String specifying the basic translational connection type. Possible values are:
- "NONE"
- "ACCELEROMETER"
- "AXIAL"
- "CARTESIAN"
- "JOIN"
- "LINK"
- "PROJECTION_CARTESIAN"
- "RADIAL_THRUST"
- "SLIDE_PLANE"
- "SLOT"

The default value is "NONE".

You cannot include the *translationalType* argument if *assembledType* is given a value other than "NONE". At least one of the arguments *assembledType*, *translationalType*, or *rotationalType* must be given an value other than "NONE".

*integration*

An odb_String specifying the time integration scheme to use for analysis. This argument is applicable only to an Abaqus/Explicit analysis. Possible values are "UNSPECIFIED", "IMPLICIT", and "EXPLICIT". The default value is "UNSPECIFIED".

*u1ReferenceLength*

The string "NONE" or a Double specifying the reference length associated with constitutive response for the first component of relative motion. The default value is "NONE".

*u2ReferenceLength*

The string "NONE" or a Double specifying the reference length associated with constitutive response for the second component of relative motion. The default value is "NONE".

*u3ReferenceLength*

The string "NONE" or a Double specifying the reference length associated with constitutive response for the third component of relative motion. The default value is "NONE".

*ur1ReferenceAngle*

The string "NONE" or a Double specifying the reference angle in degrees associated with constitutive response for the fourth component of relative motion. The default value is "NONE".

*ur2ReferenceAngle*

The string "NONE" or a Double specifying the reference angle in degrees associated with constitutive response for the fifth component of relative motion. The default value is "NONE".

*ur3ReferenceAngle*

The string "NONE" or a Double specifying the reference angle in degrees associated with constitutive response for the sixth component of relative motion. The default value is "NONE".

*massPerLength*

The string "NONE" or a Double specifying the mass per unit reference length of belt material. This argument is applicable only when *assembledType*="SLIPRING", and must be specified in that case. The default value is "NONE".

*contactAngle*

The string "NONE" or a Double specifying the contact angle made by the belt wrapping around node b. This argument is applicable only to an Abaqus/Explicit analysis, and only when *assembledType*="SLIPRING". The default value is "NONE".

*materialFlowFactor*

A Double specifying the scaling factor for material flow at node b. This argument is applicable only when *assembledType*="RETRACTOR" or *rotationalType*="FLOW_CONVERTER". The default value is 1.0.

*regularize*

A Boolean specifying whether or not all tabular data associated with the *behaviorOptions* will be regularized. This argument is applicable only for an Abaqus/Explicit analysis. The default value is true.

*defaultTolerance*

A Boolean specifying whether or not the default regularization tolerance will be used for all tabular data associated with the *behaviorOptions*. This argument is applicable only for an Abaqus/Explicit analysis and only if *regularize*=true. The default value is true.

*regularization*

A Double specifying the regularization increment to be used for all tabular data associated with the *behaviorOptions*. This argument is applicable only for an Abaqus/Explicit analysis and only if *regularize*=true and *defaultTolerance*=false. The default value is 0.03.

*extrapolation*

An odb_String specifying the extrapolation technique to be used for all tabular data associated with the *behaviorOptions*. Possible values are "CONSTANT" and "LINEAR". The default value is "CONSTANT".

*behaviorOptions*

A sequence of [ConnectorBehaviorOption](pt02ch58pyo01.md) objects.

**Return value**

A ConnectorSection object.

**Exceptions**

InvalidNameError and RangeError.

### 63.8.2 getVertices()

This method returns a sequence consisting of tuples of coordinates of the connector's endpoints.

**Path**

```
sectionApi.getVertices
```

**Prototype**

```
odb_ConnectorSection&
getVertices();
```

**Return value**

A sequence of tuples of floats.

**Exceptions**

None.

### 63.8.3 Members

The ConnectorSection object has members with the same names and descriptions as the arguments to the [ConnectorSection](pt02ch63pyo08.md#ker-connectorsection-connectorsection-cpp) method.

### 63.8.4 Corresponding analysis keywords

| [*CONNECTOR SECTION](../key/key-link.md#usb-kws-mconnectorsection) |
| --- |
| [*CONNECTOR BEHAVIOR](../key/key-link.md#usb-kws-mconnectorbehavior) |
| [*CONNECTOR CONSTITUTIVE REFERENCE](../key/key-link.md#usb-kws-mconnectorconstref) |




