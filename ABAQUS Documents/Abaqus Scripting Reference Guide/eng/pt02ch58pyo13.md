# 58.13 DerivedComponent object







A DerivedComponent object describes user-customized components for use in defining [ConnectorFriction](pt02ch58pyo07.md) and [Potential](pt02ch60pyo83.md) objects.

**Access**

```
sectionApi.sections()[*name*].behaviorOptions(*i*).connectorPotentials(*i*)\
.derivedComponent()
sectionApi.sections()[*name*].behaviorOptions(*i*).derivedComponent()
sectionApi.sections()[*name*].behaviorOptions(*i*).evolutionPotentials(*i*)\
.derivedComponent()
sectionApi.sections()[*name*].behaviorOptions(*i*).initiationPotentials(*i*)\
.derivedComponent()
```

### 58.13.1 DerivedComponent()

This method creates a DerivedComponent object.

**Path**

```
sectionApi.sections()[*name*].behaviorOptions(*i*).connectorPotentials(*i*)\
.DerivedComponent
sectionApi.sections()[*name*].behaviorOptions(*i*).DerivedComponent
sectionApi.sections()[*name*].behaviorOptions(*i*).evolutionPotentials(*i*)\
.DerivedComponent
sectionApi.sections()[*name*].behaviorOptions(*i*).initiationPotentials(*i*)\
.DerivedComponent
```

**Prototype**

```
odb_DerivedComponent&
DerivedComponent();
```

**Return value**

A DerivedComponent object.

**Exceptions**

ValueError and TextError.

### 58.13.2 setValues(...)

This method modifies the DerivedComponent object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DerivedComponent](pt02ch58pyo13.md#ker-derivedcomponent-derivedcomponent-cpp) method.

**Return value**

None

**Exceptions**

ValueError.

### 58.13.3 Members

The DerivedComponent object can have the following member:

**Prototype**

```
odb_SequenceCDCTerm cdcTerms() const;
odb_CDCTerm cdcTerms(int index) const;
```

*cdcTerms*

A sequence of [CDCTerm](pt02ch58pyo02.md) objects.

### 58.13.4 Corresponding analysis keywords

| [*CONNECTOR DERIVED COMPONENT](../key/key-link.md#usb-kws-mconnectorderivedcomp) |
| --- |




