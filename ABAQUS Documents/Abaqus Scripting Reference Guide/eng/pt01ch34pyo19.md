# 34.19 OdbPart object







The OdbPart               object is similar to the kernel Part object and contains nodes and elements, but not geometry.

**Access**

```
import odbAccess
session.odbs[*name*].parts[*name*]
```

### 34.19.1 Part(...)

This method creates an OdbPart                     object. Nodes and elements are added to this object at a later stage.

**Path**

```
session.odbs[*name*].Part
```

**Required arguments**

*name*

A String specifying the part name.

*embeddedSpace*

A SymbolicConstant specifying the dimensionality of the [Part](pt01ch37pyo01.md)                  object.                 Possible values are THREE_D, TWO_D_PLANAR, and AXISYMMETRIC.

*type*

A SymbolicConstant specifying the type of the [Part](pt01ch37pyo01.md)                  object.                 Possible values are DEFORMABLE_BODY and ANALYTIC_RIGID_SURFACE.

**Optional arguments**

None.

**Return value**

An OdbPart                     object.

**Exceptions**

None.

### 34.19.2 addElements(...)

This method adds elements to an OdbPart                    object using element labels and nodal connectivity.

**Warning:**Adding elements not in ascending order of their labels may cause Abaqus/Viewer to plot contours incorrectly.

**Required arguments**

*labels*

A sequence of Ints specifying the element labels.

*connectivity*

A sequence of sequences of Ints specifying the nodal connectivity.

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

None.

### 34.19.3 addElements(...)

This method adds elements to an OdbPart                    object using a sequence of element labels and nodal connectivity.

**Warning:**Adding elements not in ascending order of their labels may cause Abaqus/Viewer to plot contours incorrectly.

**Required arguments**

*elementData*

A sequence of sequences of Ints specifying the element labels and nodal connectivity, in the form ((*label*, *c1*, *c2*, *c3*, *c4*), (*label*, *c1*, *c2*, *c3*, *c4*), ...).

*type*

A String specifying the element type. The value can be user defined.

**Optional arguments**

*elementSetName*

A String specifying a name for this element set. The default value is None.

*sectionCategory*

A [SectionCategory](pt01ch34pyo27.md)                              object for this element set.

**Return value**

None

**Exceptions**

None.

### 34.19.4 addNodes(...)

This method adds nodes to an OdbPart                     object using node labels and coordinates.

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

None.

### 34.19.5 addNodes(...)

This method adds nodes to an OdbPart                     object using a sequence of node labels and coordinates.

**Warning:**Adding nodes not in ascending order of their labels may cause Abaqus/Viewer to plot contours incorrectly.

**Required argument**

*nodeData*

A sequence of tuples specifying the node labels and coordinates, in the form ((*label*, *x*, *y*, *z*), (*label*, *x*, *y*, *z*), ...).

**Optional argument**

*nodeSetName*

A String specifying a name for this node set. The default value is None.

**Return value**

None

**Exceptions**

None.

### 34.19.6 assignBeamOrientation(...)

This method assigns a beam section orientation to a region of a part instance.

**Required arguments**

*region*

An [OdbSet](pt01ch34pyo23.md)                              specifying a region on an instance.

*method*

A SymbolicConstant specifying the assignment method. Only a value of N1_COSINES                              is currently supported.

*vector*

A sequence of three Floats specifying the approximate local  ![](../graphics/ker_eqn00406.gif)                              -direction of the beam cross-section.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 34.19.7 assignMaterialOrientation(...)

This method assigns a material orientation to a region of a part instance.

**Required arguments**

*region*

An [OdbSet](pt01ch34pyo23.md)                              specifying a region on an instance.

*localCSys*

An [OdbDatumCsys](pt01ch34pyo13.md)                              object specifying the local coordinate system or `None`, indicating the global coordinate system.

**Optional arguments**

*axis*

A SymbolicConstant specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation is applied. For shells this axis is also the shell normal. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.

*angle*

A Float specifying the angle of the additional rotation. The default value is 0.0.

*stackDirection*

A SymbolicConstant specifying the stack or thickness direction of the material. Possible values are STACK_1, STACK_2, STACK_3, and STACK_ORIENTATION. The default value is STACK_3.

**Return value**

None

**Exceptions**

None.

### 34.19.8 assignRebarOrientation(...)

This method assigns a rebar reference orientation to a region of a part instance.

**Required arguments**

*region*

An [OdbSet](pt01ch34pyo23.md)                              specifying a region on an instance.

*localCsys*

An [OdbDatumCsys](pt01ch34pyo13.md)                              object specifying the local coordinate system or `None`, indicating the global coordinate system.

**Optional arguments**

*axis*

A SymbolicConstant specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation is applied. For shells this axis is also the shell normal. Possible values are AXIS_1, AXIS_2, and AXIS_3. The default value is AXIS_1.

*angle*

A Float specifying the angle of the additional rotation. The default value is 0.0.

**Return value**

None

**Exceptions**

None.

### 34.19.9 getElementFromLabel(...)

This method is used to retrieved an element with a specific label from a part object.

**Required argument**

*label*

An Int specifying the element label.

**Optional arguments**

None.

**Return value**

An [OdbMeshElement](pt01ch34pyo17.md)                     object.

**Exceptions**

If no element with the specified label exists:

```
OdbError: Invalid element label
```

### 34.19.10 getNodeFromLabel(...)

This method is used to retrieved a node with a specific label from a part object.

**Required argument**

*label*

An Int specifying the node label.

**Optional arguments**

None.

**Return value**

An [OdbMeshNode](pt01ch34pyo18.md)                     object.

**Exceptions**

If no node with the specified label exists:

```
OdbError: Invalid node label
```

### 34.19.11 AnalyticRigidSurf2DPlanar(...)

This method is used to define a two-dimensional [AnalyticSurface](pt01ch34pyo02.md)                     object on the part object.

**Required arguments**

*name*

The name of the analytic surface.

*profile*

A sequence of [AnalyticSurfaceSegment](pt01ch34pyo03.md)                              objects or an [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md)                              object.

**Optional argument**

*filletRadius*

A Double specifying the radius of curvature to smooth discontinuities between adjoining segments. The default value is 0.0.

**Return value**

None

**Exceptions**

If OdbPart                           is of type THREE_D: 

```
OdbError: 2D-Planar Analytic Rigid Surface can be defined only if the part is of type                             TWO_D_PLANAR                            or                             AXISYMMETRIC.                         
```

### 34.19.12 AnalyticRigidSurfExtrude(...)

This method is used to define a three-dimensional cylindrical [AnalyticSurface](pt01ch34pyo02.md)                     on the part object.

**Required arguments**

*name*

The name of the analytic surface.

*profile*

A sequence of [AnalyticSurfaceSegment](pt01ch34pyo03.md)                              objects or an [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md)                              object.

**Optional argument**

*filletRadius*

A Double specifying the radius of curvature to smooth discontinuities between adjoining segments. The default value is 0.0.

**Return value**

None

**Exceptions**

If OdbPart                           is not of type THREE_D:

```
OdbError:  Analytic Rigid Surface of type                            CYLINDER                            can be defined only if the part is of type                             THREE_D.                         
```

### 34.19.13 AnalyticRigidSurfRevolve(...)

This method is used to define a three-dimensional [AnalyticSurface](pt01ch34pyo02.md)                     of revolution on the part object.

**Required arguments**

*name*

The name of the analytic surface.

*profile*

A sequence of [AnalyticSurfaceSegment](pt01ch34pyo03.md)                              objects or an [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md)                              object.

**Optional argument**

*filletRadius*

A Double specifying the radius of curvature to smooth discontinuities between adjoining segments. The default value is 0.0.

**Return value**

None

**Exceptions**

If OdbPart                           is not of type THREE_D:

```
OdbError:  Analytic Rigid Surface of type                             REVOLUTION                            can be defined only if the part is of type                             THREE_D.                         
```

### 34.19.14 RigidBody(...)

This method defines an [OdbRigidBody](pt01ch34pyo21.md)                     on the part object.

**Required argument**

*referenceNode*

An [OdbSet](pt01ch34pyo23.md)                              specifying the reference node assigned to the rigid body.

**Optional arguments**

*position*

A symbolic constant specify if the location of the reference node is to be defined by the user. Possible values are INPUT and CENTER_OF_MASS. The default value is INPUT.

*isothermal*

A Boolean specifying an isothermal rigid body.  The default value is OFF. This parameter is used only for a fully-coupled thermal stress analysis.

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

### 34.19.15 Members

The OdbPart object has members with the same names and descriptions as the arguments to the [Part](pt01ch34pyo19.md#ker-odbpart-part-pyc) method.

In addition, the OdbPart object can have the following members:

*nodes*

An [OdbMeshNodeArray](pt01ch34pyo18.md) object.

*elements*

An [OdbMeshElementArray](pt01ch34pyo17.md) object.

*nodeSets*

A repository of [OdbSet](pt01ch34pyo23.md) objects specifying node sets.

*elementSets*

A repository of [OdbSet](pt01ch34pyo23.md) objects specifying element sets.

*surfaces*

A repository of [OdbSet](pt01ch34pyo23.md) objects specifying surfaces.

*sectionAssignments*

A [SectionAssignmentArray](pt01ch44pyo01.md) object.

*beamOrientations*

A [BeamOrientationArray](pt01ch34pyo04.md) object.

*materialOrientations*

A [MaterialOrientationArray](pt01ch44pyo04.md) object.

*rebarOrientations*

A [RebarOrientationArray](pt01ch34pyo25.md) object.

*rigidBodies*

An [OdbRigidBodyArray](pt01ch34pyo21.md) object.

*analyticSurface*

An [AnalyticSurface](pt01ch34pyo02.md) object specifying analytic Surface defined on the instance.




