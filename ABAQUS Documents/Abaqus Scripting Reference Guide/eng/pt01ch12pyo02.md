# 12.2 CDCTerm object







The CDCTerm object is used to create contributing terms for a [DerivedComponent](pt01ch12pyo13.md) object.  	    

**Access**

```
import section
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.cdcTerms[*i*]
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.cdcTerms[*i*]
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.cdcTerms[*i*]
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.cdcTerms[*i*]
import odbSection
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.cdcTerms[*i*]
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.cdcTerms[*i*]
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.cdcTerms[*i*]
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.cdcTerms[*i*]
```

### 12.2.1 CDCTerm(...)

This method creates a CDCTerm object.

**Path**

```
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.CDCTerm
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.CDCTerm
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.CDCTerm
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.CDCTerm
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent.CDCTerm
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent\
.CDCTerm
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent.CDCTerm
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent.CDCTerm
```

**Required arguments**

*intrinsicComponents*

A sequence of Ints specifying the components of relative motion for which the contributing term is defined. Possible values are 1 ![](../graphics/ker_eqn00013.gif) *intrinsicComponents* ![](../graphics/ker_eqn00013.gif) 6. Only available components can be specified if the DerivedComponent object is being referenced by a Potential object. This is not the case if the DerivedComponent object is referenced by a ConnectorFriction object directly. The default value is an empty sequence.

*table*

A sequence of sequences of Floats specifying components numbers and temperature and field values. Each sequence of the table data specifies: 		    
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

A SymbolicConstant specifying the method for combining contributing terms: square root of a sum of the squares, direct sum, or Macauley sum. Possible values are RSS, SUM, and MACAULEY. The default value is RSS.

*termSign*

A SymbolicConstant specifying the overall sign for the contributing term. Possible values are POSITIVE and NEGATIVE. The default value is POSITIVE.

*localDependency*

A Boolean specifying whether the table data depend on either components of relative position or components of constitutive relative motion. The default value is OFF.

*indepCompType*

A SymbolicConstant specifying whether localDependency refers to components of relative position or components of constitutive relative motion. Possible values are POSITION and MOTION. The default value is POSITION.

The *indepCompType* argument applies only if *localDependency*=ON.

*indepComponents*

A sequence of Ints specifying the independent components included in the derived component definition. Possible values are 1 ![](../graphics/ker_eqn00013.gif) *indepComponents* ![](../graphics/ker_eqn00013.gif) 6. Only available components can be specified. The *indepComponents* argument applies only if *localDependency*=ON. The default value is an empty sequence.

*tempDependency*

A Boolean specifying whether the table data depend on temperature. The default value is OFF.

*fieldDependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Return value**

A CDCTerm object.

**Exceptions**

ValueError and TextError.

### 12.2.2 setValues(...)

This method modifies the CDCTerm object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CDCTerm](pt01ch12pyo02.md#ker-cdcterm-cdcterm-pyc) method.

**Return value**

None

**Exceptions**

ValueError.

### 12.2.3 Members

The CDCTerm object has members with the same names and descriptions as the arguments to the [CDCTerm](pt01ch12pyo02.md#ker-cdcterm-cdcterm-pyc) method.

In addition, the CDCTerm object can have the following member:

*options*

A [ConnectorOptions](pt01ch12pyo09.md) object specifying the [ConnectorOptions](pt01ch12pyo09.md) used to define tabular options for this [ConnectorBehaviorOption](pt01ch12pyo01.md).




