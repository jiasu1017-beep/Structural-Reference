# 61.28 SectionPoint object







The SectionPoint object describes the location of a section point within a section category.

**Access**

```
odb.parts()[*name*].elements(*i*).sectionCategory().sectionPoints(*i*)
odb.parts()[*name*].elementSets()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.parts()[*name*].nodeSets()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.parts()[*name*].surfaces()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.rootAssembly().elements(*i*).sectionCategory().sectionPoints(*i*)
odb.rootAssembly().elementSets()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.rootAssembly().instances()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.rootAssembly().instances()[*name*].elementSets()[*name*].elements(*i*)\
.sectionCategory().sectionPoints(*i*)
odb.rootAssembly().instances()[*name*].nodeSets()[*name*].elements(*i*)\
.sectionCategory().sectionPoints(*i*)
odb.rootAssembly().instances()[*name*].surfaces()[*name*].elements(*i*)\
.sectionCategory().sectionPoints(*i*)
odb.rootAssembly().nodeSets()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.rootAssembly().surfaces()[*name*].elements(*i*).sectionCategory()\
.sectionPoints(*i*)
odb.sectionCategories()[*name*].sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].locations(*i*)\
.sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elements(*i*).sectionCategory().sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elementSets()[*name*].elements(*i*).sectionCategory().sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodeSets()[*name*].elements(*i*).sectionCategory().sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.surfaces()[*name*].elements(*i*).sectionCategory().sectionPoints(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).sectionPoint()
```

### 61.28.1 SectionPoint(...)

This method creates a SectionPoint object.

**Path**

```
odb.sectionCategories()[*name*].SectionPoint
```

**Prototype**

```
odb_SectionPoint&
SectionPoint(int number,
             const odb_String& description);
```

**Required arguments**

*number*

An Int specifying the number of the section point. See ["Beam elements," Section 29.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbebeam), and ["Shell elements," Section 29.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbeshell), for the numbering convention.

*description*

An odb_String specifying the description of the section point.

**Optional arguments**

None.

**Return value**

A SectionPoint object.

**Exceptions**

None.

### 61.28.2 Members

The SectionPoint object has members with the same names and descriptions as the arguments to the [SectionPoint](pt02ch61pyo28.md#ker-sectionpoint-sectionpoint-cpp) method.

**Prototype**

```
int number() const;
const odb_String description() const;
```




