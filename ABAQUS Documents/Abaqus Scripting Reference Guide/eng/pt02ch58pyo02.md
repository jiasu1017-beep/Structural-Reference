# 58.2 CDCTerm object







The CDCTerm object is used to create contributing terms for a [DerivedComponent](pt02ch58pyo13.md) object.  	    

**Access**

```
sectionApi.sections()[*name*].behaviorOptions(*i*).connectorPotentials(*i*)\
.derivedComponent().cdcTerms(*i*)
sectionApi.sections()[*name*].behaviorOptions(*i*).derivedComponent()\
.cdcTerms(*i*)
sectionApi.sections()[*name*].behaviorOptions(*i*).evolutionPotentials(*i*)\
.derivedComponent().cdcTerms(*i*)
sectionApi.sections()[*name*].behaviorOptions(*i*).initiationPotentials(*i*)\
.derivedComponent().cdcTerms(*i*)
```

### 58.2.1 CDCTerm(...)

This method creates a CDCTerm object.

**Path**

```
sectionApi.sections()[*name*].behaviorOptions(*i*).connectorPotentials(*i*)\
.derivedComponent().CDCTerm
sectionApi.sections()[*name*].behaviorOptions(*i*).derivedComponent()\
.CDCTerm
sectionApi.sections()[*name*].behaviorOptions(*i*).evolutionPotentials(*i*)\
.derivedComponent().CDCTerm
sectionApi.sections()[*name*].behaviorOptions(*i*).initiationPotentials(*i*)\
.derivedComponent().CDCTerm
```

**Prototype**

```
odb_CDCTerm&
CDCTerm(const odb_SequenceInt& intrinsicComponents,
        const odb_SequenceSequenceDouble& table,
        const odb_String& termOperator,
        const odb_String& termSign,
        bool localDependency,
        const odb_String& indepCompType,
        const odb_SequenceInt& indepComponents,
        bool tempDependency,
        int fieldDependencies);
```

**Required arguments**

*intrinsicComponents*

An odb_SequenceInt specifying the components of relative motion for which the contributing term is defined. Possible values are 1 ![](../graphics/ker_eqn00013.gif) *intrinsicComponents* ![](../graphics/ker_eqn00013.gif) 6. Only available components can be specified if the DerivedComponent object is being referenced by a Potential object. This is not the case if the DerivedComponent object is referenced by a ConnectorFriction object directly. The default value is an empty sequence.

*table*

An odb_SequenceSequenceDouble specifying components numbers and temperature and field values. Each sequence of the table data specifies: 		    
- The first intrinsic component number.
- If applicable, the second intrinsic component number.
- Etc.
- If applicable, the first independent component number.
- If applicable, the second independent component number.
- Etc.
- If applicable, the temperature value.
- If applicable, the value of the first field variable.
- If applicable, the value of the second field variable.
- Etc.

The default value is an empty sequence.

**Optional arguments**

*termOperator*

An odb_String specifying the method for combining contributing terms: square root of a sum of the squares, direct sum, or Macauley sum. Possible values are "RSS", "SUM", and "MACAULEY". The default value is "RSS".

*termSign*

An odb_String specifying the overall sign for the contributing term. Possible values are "POSITIVE" and "NEGATIVE". The default value is "POSITIVE".

*localDependency*

A Boolean specifying whether the table data depend on either components of relative position or components of constitutive relative motion. The default value is false.

*indepCompType*

An odb_String specifying whether localDependency refers to components of relative position or components of constitutive relative motion. Possible values are "POSITION" and "MOTION". The default value is "POSITION".

The *indepCompType* argument applies only if *localDependency*=true.

*indepComponents*

An odb_SequenceInt specifying the independent components included in the derived component definition. Possible values are 1 ![](../graphics/ker_eqn00013.gif) *indepComponents* ![](../graphics/ker_eqn00013.gif) 6. Only available components can be specified. The *indepComponents* argument applies only if *localDependency*=true. The default value is an empty sequence.

*tempDependency*

A Boolean specifying whether the table data depend on temperature. The default value is false.

*fieldDependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Return value**

A CDCTerm object.

**Exceptions**

ValueError and TextError.

### 58.2.2 setValues(...)

This method modifies the CDCTerm object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CDCTerm](pt02ch58pyo02.md#ker-cdcterm-cdcterm-cpp) method.

**Return value**

None

**Exceptions**

ValueError.

### 58.2.3 Members

The CDCTerm object has members with the same names and descriptions as the arguments to the [CDCTerm](pt02ch58pyo02.md#ker-cdcterm-cdcterm-cpp) method.

In addition, the CDCTerm object can have the following member:

**Prototype**

```
odb_ConnectorOptions options() const;
```

*options*

A [ConnectorOptions](pt02ch58pyo09.md) object specifying the [ConnectorOptions](pt02ch58pyo09.md) used to define tabular options for this [ConnectorBehaviorOption](pt02ch58pyo01.md).




