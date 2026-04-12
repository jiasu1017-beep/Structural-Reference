# 34.12 OdbAssembly object







The OdbAssembly               object has no constructor; it is created automatically when an [Odb](pt01ch34pyo01.md)               object is created. Abaqus creates the *rootAssembly*               member when an [Odb](pt01ch34pyo01.md)               object is created.

**Access**

```
import odbAccess
session.odbs[*name*].rootAssembly
```

### 34.12.1 ConnectorOrientation(...)

This method assigns a connector orientation to a connector region.

**Required argument**

*region*

An [OdbSet](pt01ch34pyo23.md)                              specifying a region.

**Optional arguments**

*localCsys1*

An [OdbDatumCsys](pt01ch34pyo13.md)                              object specifying the first connector node local coordinate system or `None`, indicating the global coordinate system.

*axis1*

A SymbolicConstant specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation of the first connector node is applied.  Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.

*angle1*

A Float specifying the angle of the additional rotation about the first connector node axis. The default value is 0.0.

*orient2sameAs1*

A Boolean specifying whether the same orientation settings should be used for the second node of the connector.  The default value is OFF.

*localCsys2*

An [OdbDatumCsys](pt01ch34pyo13.md)                              object specifying the second connector node local coordinate system or `None`, indicating the global coordinate system.

*axis2*

A SymbolicConstant specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation of the second connector node is applied.  Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.

*angle2*

A Float specifying the angle of the additional rotation about the second connector node axis. The default value is 0.0.

**Return value**

None

**Exceptions**

If *region*                           is not an element set:

```
OdbError: Connector orientation assignment requires element set.
```

### 34.12.2 SectionAssignment(...)

This method is used to assign a section to a region on an instance.  Only connector sections can be assigned at the assembly level.

**Required arguments**

*region*

An [OdbSet](pt01ch34pyo23.md)                              specifying a region.

*section*

A [Section](pt01ch46pyo01.md)                              object.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

If *region*                           is not an element set:

```
OdbError: Section assignment requires element set.
```

### 34.12.3 addElements(...)

This method is used to define elements using nodes defined at the OdbAssembly                     and/or [OdbInstance](pt01ch34pyo15.md)                    level. For connector elements connected to ground, specify the lone node in the connectivity. The position of the ground node cannot be specified. This is a limitation.

**Warning:**Adding elements not in ascending order of their labels may cause Abaqus/Viewer to plot contours incorrectly.

**Required arguments**

*labels*

A sequence of Ints specifying the element labels.

*connectivity*

A sequence of sequences of Ints specifying the nodal connectivity.

*instanceNames*

A sequence of Strings specifying the instanceNames of each node in the nodal connectivity array. If the node is defined at the assembly level, the instance name should be an empty string

*type*

A String specifying the element type.

**Optional arguments**

*elementSetName*

A String specifying a name for this element set. The default value is the empty string.

*sectionCategory*

A [SectionCategory](pt01ch34pyo27.md)                              object for this element set.

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

### 34.12.4 addNodes(...)

This method adds nodes to the OdbAssembly                     object using node labels and coordinates.

**Warning:**Adding nodes not in ascending order of their labels may cause Abaqus/Viewer to plot contours incorrectly.

**Required arguments**

*labels*

A sequence of Ints specifying the node labels.

*coordinates*

A sequence of sequences of Floats specifying the nodal coordinates.

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

### 34.12.5 RigidBody(...)

This method defines an [OdbRigidBody](pt01ch34pyo21.md)                     on the assembly.

**Required argument**

*referenceNode*

An [OdbSet](pt01ch34pyo23.md)                              specifying the reference node assigned to the rigid body.

**Optional arguments**

*position*

A symbolic constant specify if the location of the reference node is to be defined by the user. Possible values are INPUT and CENTER_OF_MASS. The default value is INPUT.

*isothermal*

A Boolean specifying an isothermal rigid body.  The default value is OFF. This parameter is used only for a fully coupled thermal stress analysis.

*elset*

An [OdbSet](pt01ch34pyo23.md)                              specifying an element set assigned to the rigid body.

*pinNodes*

An [OdbSet](pt01ch34pyo23.md)                              specifying pin-type nodes assigned to the rigid body.

*tieNodes*

An [OdbSet](pt01ch34pyo23.md)                              specifying tie-type nodes assigned to the rigid body.

**Return value**

None

**Exceptions**

If *referenceNode*                           is not a node set:

```
OdbError: Rigid body definition requires a node set.
```

### 34.12.6 Members

The OdbAssembly object can have the following members:

*instances*

A repository of [OdbInstance](pt01ch34pyo15.md) objects.

*nodeSets*

A repository of [OdbSet](pt01ch34pyo23.md) objects specifying node sets.

*elementSets*

A repository of [OdbSet](pt01ch34pyo23.md) objects specifying element sets.

*surfaces*

A repository of [OdbSet](pt01ch34pyo23.md) objects specifying surfaces.

*nodes*

An [OdbMeshNodeArray](pt01ch34pyo18.md) object.

*elements*

An [OdbMeshElementArray](pt01ch34pyo17.md) object.

*datumCsyses*

A repository of [OdbDatumCsys](pt01ch34pyo13.md) objects.

*sectionAssignments*

A [SectionAssignmentArray](pt01ch44pyo01.md) object.

*rigidBodies*

An [OdbRigidBodyArray](pt01ch34pyo21.md) object.

*pretensionSections*

An [OdbPretensionSectionArray](pt01ch34pyo20.md) object.

*connectorOrientations*

A [ConnectorOrientationArray](pt01ch06pyo02.md) object.




