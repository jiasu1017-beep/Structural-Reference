# 58.11 ConnectorPotential object







The ConnectorPotential object is used to define a restricted set of mathematical functions to represent yield or limiting surfaces in the space spanned by connector available components. It can be used only in conjunction with [ConnectorDamage](pt02ch58pyo03.md), [ConnectorFriction](pt02ch58pyo07.md), and [ConnectorPlasticity](pt02ch58pyo10.md) objects. Because the [ConnectorDamage](pt02ch58pyo03.md) object contains two separate ConnectorPotential repositories (one for damage initiation and one for damage evolution), there are two ConnectorPotential constructors associated with that behavior—IniPotential and EvoPotential.

**Access**

```
sectionApi.sections()[*name*].behaviorOptions(*i*).connectorPotentials(*i*)
sectionApi.sections()[*name*].behaviorOptions(*i*).evolutionPotentials(*i*)
sectionApi.sections()[*name*].behaviorOptions(*i*).initiationPotentials(*i*)
```

### 58.11.1 ConnectorPotential(...)

This method creates a connector potential object to be used in conjunction with an allowable connector behavior option.

**Path**

```
sectionApi.sections()[*name*].behaviorOptions(*i*).ConnectorPotential
```

**Prototype**

```
odb_ConnectorPotential&
ConnectorPotential(const odb_String& componentStyle,
                   int componentNumber,
                   const odb_String& sign,
                   double scaleFactor,
                   double positiveExponent,
                   double shiftFactor,
                   const odb_String& hFunction);
```

**Required arguments**

None.

**Optional arguments**

*componentStyle*

An odb_String specifying whether a component number or the name of the [DerivedComponent](pt02ch58pyo13.md) object will be used in the contribution. Possible values are "COMPONENT_NUMBER" and "DERIVED_COMPONENT". The default value is "COMPONENT_NUMBER".

*componentNumber*

An Int specifying the component number used in the contribution. This argument is applicable only if *componentStyle*="COMPONENT_NUMBER". Possible values are 1 ![](../graphics/ker_eqn00013.gif) *componentNumber* ![](../graphics/ker_eqn00013.gif) 6. Only available components can be specified. The default value is 0.

*sign*

An odb_String specifying the sign of the contribution. Possible values are "POSITIVE" and "NEGATIVE". The default value is "POSITIVE".

*scaleFactor*

A Double specifying the scaling factor for the contribution. The default value is 1.0.

*positiveExponent*

A Double specifying the positive exponent for the contribution. The default value is 2.0.

This argument is ignored if the potential operator of the invoking behavior option is set to "MAXIMUM".

*shiftFactor*

A Double specifying the shift factor for the contribution. The default value is 0.0.

*hFunction*

An odb_String specifying the H function of the contribution: either absolute value, Macauley bracket, or the identity function. Possible values are "ABS", "MACAULEY", and "IDENTITY". The default value is "ABS".

The value of "IDENTITY" can be used only if *positiveExponent*=1.0 and the potential exponent of the invoking behavior option is also 1.0 (i.e., the potential operator of the invoking behavior option must be "SUM").

**Return value**

A ConnectorPotential object.

**Exceptions**

ValueError and TextError.

### 58.11.2 setValues(...)

This method modifies the ConnectorPotential object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ConnectorPotential](pt02ch58pyo11.md#ker-connectorpotential-connectorpotential-cpp) method.

**Return value**

None

**Exceptions**

ValueError.

### 58.11.3 Members

The ConnectorPotential object has members with the same names and descriptions as the arguments to the [ConnectorPotential](pt02ch58pyo11.md#ker-connectorpotential-connectorpotential-cpp) method.

In addition, the ConnectorPotential object can have the following member:

**Prototype**

```
odb_DerivedComponent derivedComponent() const;
```

*derivedComponent*

A [DerivedComponent](pt02ch58pyo13.md) object specifying the [DerivedComponent](pt02ch58pyo13.md) used in the contribution. This argument is applicable only if *componentStyle*="DERIVED_COMPONENT".

### 58.11.4 Corresponding analysis keywords

| [*CONNECTOR POTENTIAL](../key/key-link.md#usb-kws-mconnectorpotential) |
| --- |




