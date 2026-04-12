# 61.21 OdbPretensionSection object







The pretension section object is used to define an assembly load. It associates a pretension node with a pretension section.

**Access**

```
odb.rootAssembly().pretensionSections(*i*)
```

### 61.21.1 Members

The OdbPretensionSection object can have the following members:

**Prototype**

```
odb_Set node() const;
odb_Set element() const;
odb_Set surface() const;
odb_SequenceFloat normal() const;
float normal(int index) const;
```

*node*

An [OdbSet](pt02ch61pyo24.md) object specifying the node set containing the pretension node.

*element*

An [OdbSet](pt02ch61pyo24.md) object specifying the element set that defines the pretension section.

*surface*

An [OdbSet](pt02ch61pyo24.md) object specifying the surface set that defines the pretension section.

*normal*

An odb_SequenceFloat specifying the components of the normal to the pretension section.




