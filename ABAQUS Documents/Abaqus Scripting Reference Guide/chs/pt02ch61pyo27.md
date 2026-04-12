# 61.27 SectionCategory object







The SectionCategory object is used to group regions of the model with like sections. Section definitions that contain the same number of section points or integration points are grouped together.

To access data for a particular section definition, use the individual [Section](pt02ch63pyo01.md) objects in the output database. For more information, see [Chapter 8, "Beam Section profile commands](pt01ch08.md),” and [Chapter 46, "Section commands](pt01ch46.md).”

**Access**

```
odb.parts()[*name*].elements(*i*).sectionCategory()
odb.parts()[*name*].elementSets()[*name*].elements(*i*).sectionCategory()
odb.parts()[*name*].nodeSets()[*name*].elements(*i*).sectionCategory()
odb.parts()[*name*].surfaces()[*name*].elements(*i*).sectionCategory()
odb.rootAssembly().elements(*i*).sectionCategory()
odb.rootAssembly().elementSets()[*name*].elements(*i*).sectionCategory()
odb.rootAssembly().instances()[*name*].elements(*i*).sectionCategory()
odb.rootAssembly().instances()[*name*].elementSets()[*name*].elements(*i*)\
.sectionCategory()
odb.rootAssembly().instances()[*name*].nodeSets()[*name*].elements(*i*)\
.sectionCategory()
odb.rootAssembly().instances()[*name*].surfaces()[*name*].elements(*i*)\
.sectionCategory()
odb.rootAssembly().nodeSets()[*name*].elements(*i*).sectionCategory()
odb.rootAssembly().surfaces()[*name*].elements(*i*).sectionCategory()
odb.sectionCategories()[*name*]
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elements(*i*).sectionCategory()
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.elementSets()[*name*].elements(*i*).sectionCategory()
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.nodeSets()[*name*].elements(*i*).sectionCategory()
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.surfaces()[*name*].elements(*i*).sectionCategory()
```

### 61.27.1 SectionCategory(...)

This method creates a SectionCategory object.

**Path**

```
odb.SectionCategory
```

**Prototype**

```
odb_SectionCategory&
SectionCategory(const odb_String& name,
                const odb_String& description);
```

**Required arguments**

*name*

An odb_String specifying the name of the category.

*description*

An odb_String specifying the description of the category.

**Optional arguments**

None.

**Return value**

A SectionCategory object.

**Exceptions**

None.

### 61.27.2 Members

The SectionCategory object has members with the same names and descriptions as the arguments to the [SectionCategory](pt02ch61pyo27.md#ker-sectioncategory-sectioncategory-cpp) method.

In addition, the SectionCategory object can have the following member:

**Prototype**

```
odb_String name() const;
odb_String description() const;
const odb_SectionPoint& sectionPoints(int index) const;
const odb_SequenceSectionPoint& sectionPoints() const;
```

*sectionPoints*

A sequence of [SectionPoint](pt02ch61pyo28.md) objects.




