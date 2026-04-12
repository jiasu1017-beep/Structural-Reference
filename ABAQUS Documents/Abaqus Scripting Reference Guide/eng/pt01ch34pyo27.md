# 34.27 SectionCategory object







The SectionCategory object is used to group regions of the model with like sections. Section definitions that contain the same number of section points or integration points are grouped together.

To access data for a particular section definition, use the individual [Section](pt01ch46pyo01.md) objects in the output database. For more information, see [Chapter 8, "Beam Section profile commands](pt01ch08.md),” and [Chapter 46, "Section commands](pt01ch46.md).”

**Access**

```
import odbAccess
session.odbs[*name*].parts[*name*].elements[*i*].sectionCategory
session.odbs[*name*].parts[*name*].elementSets[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].parts[*name*].nodeSets[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].parts[*name*].surfaces[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].rootAssembly.elements[*i*].sectionCategory
session.odbs[*name*].rootAssembly.elementSets[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].rootAssembly.instances[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].rootAssembly.instances[*name*].elementSets[*name*]\
.elements[*i*].sectionCategory
session.odbs[*name*].rootAssembly.instances[*name*].nodeSets[*name*]\
.elements[*i*].sectionCategory
session.odbs[*name*].rootAssembly.instances[*name*].surfaces[*name*]\
.elements[*i*].sectionCategory
session.odbs[*name*].rootAssembly.nodeSets[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].rootAssembly.surfaces[*name*].elements[*i*]\
.sectionCategory
session.odbs[*name*].sectionCategories[*name*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elements[*i*].sectionCategory
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elementSets[*name*].elements[*i*].sectionCategory
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.nodeSets[*name*].elements[*i*].sectionCategory
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.surfaces[*name*].elements[*i*].sectionCategory
```

### 34.27.1 SectionCategory(...)

This method creates a SectionCategory object.

**Path**

```
session.odbs[*name*].SectionCategory
```

**Required arguments**

*name*

A String specifying the name of the category.

*description*

A String specifying the description of the category.

**Optional arguments**

None.

**Return value**

A SectionCategory object.

**Exceptions**

None.

### 34.27.2 Members

The SectionCategory object has members with the same names and descriptions as the arguments to the [SectionCategory](pt01ch34pyo27.md#ker-sectioncategory-sectioncategory-pyc) method.

In addition, the SectionCategory object can have the following member:

*sectionPoints*

A [SectionPointArray](pt01ch34pyo28.md) object.




