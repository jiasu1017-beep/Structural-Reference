# 12.13 DerivedComponent object







A DerivedComponent object describes user-customized components for use in defining [ConnectorFriction](pt01ch12pyo07.md) and [Potential](pt01ch29pyo83.md) objects.

**Access**

```
import section
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent
import odbSection
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].derivedComponent
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].derivedComponent
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].derivedComponent
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].derivedComponent
```

### 12.13.1 DerivedComponent()

This method creates a DerivedComponent object.

**Path**

```
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].DerivedComponent
mdb.models[*name*].sections[*name*].behaviorOptions[*i*].DerivedComponent
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].DerivedComponent
mdb.models[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].DerivedComponent
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.connectorPotentials[*i*].DerivedComponent
session.odbs[*name*].sections[*name*].behaviorOptions[*i*].DerivedComponent
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.evolutionPotentials[*i*].DerivedComponent
session.odbs[*name*].sections[*name*].behaviorOptions[*i*]\
.initiationPotentials[*i*].DerivedComponent
```

**Return value**

A DerivedComponent object.

**Exceptions**

ValueError and TextError.

### 12.13.2 setValues(...)

This method modifies the DerivedComponent object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DerivedComponent](pt01ch12pyo13.md#ker-derivedcomponent-derivedcomponent-pyc) method.

**Return value**

None

**Exceptions**

ValueError.

### 12.13.3 Members

The DerivedComponent object can have the following member:

*cdcTerms*

A [CDCTermArray](pt01ch12pyo02.md) object.

### 12.13.4 Corresponding analysis keywords

| [*CONNECTOR DERIVED COMPONENT](../key/key-link.md#usb-kws-mconnectorderivedcomp) |
| --- |




