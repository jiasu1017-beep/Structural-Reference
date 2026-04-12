# 34.20 OdbPretensionSection object







The pretension section object is used to define an assembly load. It associates a pretension node with a pretension section.

**Access**

```
import odbAccess
session.odbs[*name*].rootAssembly.pretensionSections[*i*]
```

### 34.20.1 Members

The OdbPretensionSection object can have the following members:

*node*

An [OdbSet](pt01ch34pyo23.md) object specifying the node set containing the pretension node.

*element*

An [OdbSet](pt01ch34pyo23.md) object specifying the element set that defines the pretension section.

*surface*

An [OdbSet](pt01ch34pyo23.md) object specifying the surface set that defines the pretension section.

*normal*

A tuple of Floats specifying the components of the normal to the pretension section.




