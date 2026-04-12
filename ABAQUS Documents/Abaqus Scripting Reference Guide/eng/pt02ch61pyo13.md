# 61.13 OdbAssembly object







The OdbAssembly               object has no constructor; it is created automatically when an [Odb](pt02ch61pyo01.md)               object is created. Abaqus creates the *rootAssembly*               member when an [Odb](pt02ch61pyo01.md)               object is created.

**Access**

```
odb.rootAssembly()
```

### 61.13.1 ConnectorOrientation(...)

This method assigns a connector orientation to a connector region.

**Prototype**

```
void
ConnectorOrientation(const odb_Set& region,
                     const odb_DatumCsys& csys1,
                     odb_Enum::odb_AxisEnum axis1,
                     float angle1,                     
                     const odb_DatumCsys& csys2,
                     odb_Enum::odb_AxisEnum axis2,
                     float angle2);
```

**Required arguments**

*region*

An [OdbSet](pt02ch61pyo24.md)                              specifying a region.

*csys1*

An [OdbDatumCsys](pt02ch61pyo14.md)                              object specifying the first connector node local coordinate system.

*axis1*

An odb_Enum::odb_AxisEnum specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation of the first connector node is applied.  Possible values are odb_Enum::AXIS_1, odb_Enum::AXIS_2, and odb_Enum::AXIS_3.

*angle1*

A Float specifying the angle of the additional rotation about the first connector node axis. The default value is 0.0.

*csys2*

An [OdbDatumCsys](pt02ch61pyo14.md)                              object specifying the second connector node local coordinate system.

*axis2*

An odb_Enum::odb_AxisEnum specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation of the second connector node is applied.  Possible values are odb_Enum::AXIS_1, odb_Enum::AXIS_2, and odb_Enum::AXIS_3.

*angle2*

A Float specifying the angle of the additional rotation about the second connector node axis.

**Return value**

None

**Exceptions**

If *region*                           is not an element set:

```
OdbError: Connector orientation assignment requires element set.
```

### 61.13.2 ConnectorOrientation(...)

This method assigns a connector orientation to a connector region.

**Prototype**

```

        void
        ConnectorOrientation(const odb_Set& region,
        const odb_DatumCsys& csys1,
        odb_Enum::odb_AxisEnum axis1,
        float angle1,
        bool orient2sameAs1);

```

**Required arguments**

*region*

               An [OdbSet](pt02ch61pyo24.md)                              specifying a region.             

*csys1*

               An [OdbDatumCsys](pt02ch61pyo14.md)                              object specifying the first connector node local coordinate system.             

*axis1*

               An odb_Enum::odb_AxisEnum specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation of the first connector node is applied.  Possible values are odb_Enum::AXIS_1, odb_Enum::AXIS_2, and odb_Enum::AXIS_3.             

*angle1*

A Float specifying the angle of the additional rotation about the first connector node axis.

**Optional arguments**

*orient2sameAs1*

               A Boolean specifying whether the same orientation settings should be used for the second node of the connector.  The default value is false.             

**Return value**

None

**Exceptions**

             If *region*                           is not an element set:           

```
OdbError: Connector orientation assignment requires element set.
```

### 61.13.3 SectionAssignment(...)

This method is used to assign a section to a region on an instance.  Only connector sections can be assigned at the assembly level.

**Prototype**

```
void
SectionAssignment(const odb_Set& region,
                  const odb_section& section);
```

**Required arguments**

*region*

An [OdbSet](pt02ch61pyo24.md)                              specifying a region.

*section*

A [Section](pt02ch63pyo01.md)                              object.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

If *region*                           is not an element set:

```
OdbError: Section assignment requires element set.
```

### 61.13.4 addElements(...)

This method is used to define elements using nodes defined at the OdbAssembly                     and/or [OdbInstance](pt02ch61pyo16.md)                    level. For connector elements connected to ground, specify the lone node in the connectivity. The position of the ground node cannot be specified. This is a limitation.

**Warning:**Adding elements not in ascending order of their labels may cause Abaqus/Viewer to plot contours incorrectly.

**Prototype**

```
void
addElements(const odb_SequenceInt& labels,
            const odb_SequenceSequenceInt& connectivity,
            const odb_SequenceString& instanceNames,
            const odb_String& type,
            const odb_String& elementSetName,
            const odb_SectionCategory& sectionCategory);
```

**Required arguments**

*labels*

An odb_SequenceInt specifying the element labels.

*connectivity*

An odb_SequenceSequenceInt specifying the nodal connectivity.

*instanceNames*

An odb_SequenceString specifying the instanceNames of each node in the nodal connectivity array. If the node is defined at the assembly level, the instance name should be an empty string

*type*

A String specifying the element type.

**Optional arguments**

*elementSetName*

A String specifying a name for this element set. The default value is the empty string.

*sectionCategory*

A [SectionCategory](pt02ch61pyo27.md)                              object for this element set.

**Return value**

None

**Exceptions**

Only certain element types are permitted at the assembly level. e.g., connector elements.

```
OdbError: Addition of this element type is not permitted at the assembly level
```

If length of label array does not match connectivity data length:

```
OdbError: Connectivity array must be provided for all element
```

### 61.13.5 addNodes(...)

This method adds nodes to the OdbAssembly                     object using node labels and coordinates.

**Warning:**Adding nodes not in ascending order of their labels may cause Abaqus/Viewer to plot contours incorrectly.

**Prototype**

```
void
addNodes(const odb_SequenceInt& labels,
         const odb_SequenceSequenceFloat& coordinates,
         const odb_String& nodeSetName);
```

**Required arguments**

*labels*

An odb_SequenceInt specifying the node labels.

*coordinates*

An odb_SequenceSequenceFloat specifying the nodal coordinates.

**Optional argument**

*nodeSetName*

A String specifying a name for this node set. The default value is None.

**Return value**

None

**Exceptions**

If length of labels does not match length of coordinates:

```
OdbError: Number of node labels and coordinates does not match
```

If width of coordinate array does not match assembly dimension:

```
OdbError: Node location specification does not correspond to part dimensions
```

### 61.13.6 sectionAssignments(...)

This method is used to retrieve a section assignment.

**Prototype**

```
odb_SectionAssignment
sectionAssignments(int index);
```

**Required argument**

*index*

An Int specifying the section assignment.

**Optional arguments**

None.

**Return value**

A [SectionAssignment](pt02ch62pyo01.md)                     object.

**Exceptions**

None.

### 61.13.7 RigidBody(...)

This method defines an [OdbRigidBody](pt02ch61pyo22.md)                     on the assembly.

**Prototype**

```
void
RigidBody(const odb_Set& referenceNode,
          odb_Enum::odb_PositionEnum position,
          bool isothermal,
          const odb_Set& elset,
          const odb_Set& pinNodes,
          const odb_Set& tieNodes);
```

**Required argument**

*referenceNode*

An [OdbSet](pt02ch61pyo24.md)                              specifying the reference node assigned to the rigid body.

**Optional arguments**

*position*

A symbolic constant specify if the location of the reference node is to be defined by the user. Possible values are odb_Enum::INPUT and odb_Enum::CENTER_OF_MASS. The default value is odb_Enum::INPUT.

*isothermal*

A Boolean specifying an isothermal rigid body.  The default value is false. This parameter is used only for a fully coupled thermal stress analysis.

*elset*

An [OdbSet](pt02ch61pyo24.md)                              specifying an element set assigned to the rigid body.

*pinNodes*

An [OdbSet](pt02ch61pyo24.md)                              specifying pin-type nodes assigned to the rigid body.

*tieNodes*

An [OdbSet](pt02ch61pyo24.md)                              specifying tie-type nodes assigned to the rigid body.

**Return value**

None

**Exceptions**

If *referenceNode*                           is not a node set:

```
OdbError: Rigid body definition requires a node set.
```

### 61.13.8 Members

The OdbAssembly object can have the following members:

**Prototype**

```
odb_InstanceRepository& instances();
               odb_SetRepository& nodeSets();
               odb_SetRepository& elementSets();
               odb_SetRepository& surfaces();
               odb_SequenceNode& nodes() const;
               odb_SequenceElement& elements() const;
               odb_DatumCsysRepository& datumCsyses();
               odb_SequenceSectionAssignment sectionAssignments();
               odb_SequenceConnectorOrientation connectorOrientations();
               odb_SequenceRigidBody rigidBodies();
               odb_SequencePretensionSection pretensionSections();
```

*instances*

A repository of [OdbInstance](pt02ch61pyo16.md) objects.

*nodeSets*

A repository of [OdbSet](pt02ch61pyo24.md) objects specifying node sets.

*elementSets*

A repository of [OdbSet](pt02ch61pyo24.md) objects specifying element sets.

*surfaces*

A repository of [OdbSet](pt02ch61pyo24.md) objects specifying surfaces.

*nodes*

A sequence of [OdbMeshNode](pt02ch61pyo19.md) objects.

*elements*

A sequence of [OdbMeshElement](pt02ch61pyo18.md) objects.

*datumCsyses*

A repository of [OdbDatumCsys](pt02ch61pyo14.md) objects.

*sectionAssignments*

A sequence of [SectionAssignment](pt02ch62pyo01.md) objects.

*rigidBodies*

A sequence of [OdbRigidBody](pt02ch61pyo22.md) objects.

*pretensionSections*

A sequence of [OdbPretensionSection](pt02ch61pyo21.md) objects.

*connectorOrientations*

A sequence of [ConnectorOrientation](pt02ch61pyo13.md#ker-odbassembly-connectororientation-cpp) objects.




