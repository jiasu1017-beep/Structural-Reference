# 34.17 OdbMeshElement object







 OdbMeshElement               objects are created with the `part.addElements`               or `rootAssembly.addElements`               methods.

**Access**

```
import odbAccess
session.odbs[*name*].parts[*name*].elements[*i*]
session.odbs[*name*].parts[*name*].elementSets[*name*].elements[*i*]
session.odbs[*name*].parts[*name*].nodeSets[*name*].elements[*i*]
session.odbs[*name*].parts[*name*].surfaces[*name*].elements[*i*]
session.odbs[*name*].rootAssembly.elements[*i*]
session.odbs[*name*].rootAssembly.elementSets[*name*].elements[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].elements[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].elementSets[*name*]\
.elements[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].nodeSets[*name*]\
.elements[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].surfaces[*name*]\
.elements[*i*]
session.odbs[*name*].rootAssembly.nodeSets[*name*].elements[*i*]
session.odbs[*name*].rootAssembly.surfaces[*name*].elements[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elements[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elementSets[*name*].elements[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.nodeSets[*name*].elements[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.surfaces[*name*].elements[*i*]
```

### 34.17.1 Members

The OdbMeshElement object can have the following members:

*label*

An Int specifying the element label.

*type*

A String specifying the element type.

*sectionCategory*

A [SectionCategory](pt01ch34pyo27.md) object specifying the element section properties.

*connectivity*

A tuple of Ints specifying the element connectivity. For connector elements connected to ground, the other node is repeated in the connectivity data. The position of the ground node cannot be ascertained. This is a limitation. It is important to note the difference with MeshElement object of MDB where the connectivity is node indices instead of node labels.

*instanceNames*

A tuple of Strings specifying the instance names for nodes in the element connectivity.

*instanceName*

A String specifying the instance name.




