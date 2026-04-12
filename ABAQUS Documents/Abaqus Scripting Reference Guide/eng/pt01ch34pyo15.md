# 34.15 OdbInstance object







A part instance is the usage of a part within an assembly.

**Access**

```
import odbAccess
session.odbs[*name*].rootAssembly.instances[*name*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance
```

### 34.15.1 Instance(...)

This method creates an OdbInstance                     object from an [OdbPart](pt01ch34pyo19.md)                     object.

**Path**

```
session.odbs[*name*].rootAssembly.Instance
```

**Required arguments**

*name*

A String specifying the instance name.

*object*

An [OdbPart](pt01ch34pyo19.md)                              object.

**Optional argument**

*localCoordSystem*

A sequence of sequences of three Floats specifying the rotation and translation of the part instance in the global Cartesian coordinate system. The first three sequences specify the new local coordinate system with its center at the origin.
- The first sequence specifies a point on the 1-axis.
- The second sequence specifies a point on the 2-axis.
- The third sequence specifies a point on the 3-axis.

                              The fourth sequence specifies the translation of the local coordinate system from the origin to its intended location.

For example, the following sequence moves a part 10 units in the *X*-direction with no rotation:

```
localCoordSystem = ((1, 0, 0), (0, 1, 0),
                                 (0, 0, 1), (10, 0, 0))
```

The following sequence moves a part 5 units in the *X*-direction with rotation:

```
localCoordSystem = ((0, 1, 0), (1, 0, 0),
                                 (0, 0, 1), (5, 0, 0))
```
                                 transforms a part containing the two points 
```

                                 Pt1= (1,0,0) 
                                 Pt2= (2,0,0) 

```
                                to
```

                                 Pt1 = (0, 6, 0) 
                                 Pt2 = (0, 7, 0)                      

```

**Return value**

An OdbInstance                     object.

**Exceptions**

InvalidNameError.

### 34.15.2 assignBeamOrientation(...)

This method assigns a beam section orientation to a region of a part instance.

**Required arguments**

*region*

An [OdbSet](pt01ch34pyo23.md)                              specifying a region on an instance.

*method*

A SymbolicConstant specifying the assignment method. Only a value of N1_COSINES                              is currently supported.

*vector*

A sequence of three Floats specifying the approximate local ![](../graphics/ker_eqn00406.gif)-direction of the beam cross-section.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 34.15.3 assignMaterialOrientation(...)

This method assigns a material orientation to a region of a part instance.

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

*stackDirection*

A SymbolicConstant specifying the stack or thickness direction of the material. Possible values are STACK_1, STACK_2, STACK_3, and STACK_ORIENTATION. The default value is STACK_3.

**Return value**

None

**Exceptions**

None.

### 34.15.4 assignRebarOrientation(...)

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

### 34.15.5 getElementFromLabel(...)

This method is used to retrieved an element with a specific label from an instance object.

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

### 34.15.6 getNodeFromLabel(...)

This method is used to retrieved a node with a specific label from an instance object.

**Required argument**

*label*

An Int specifying the node label.

**Optional arguments**

None.

**Return value**

An[OdbMeshNode](pt01ch34pyo18.md)                     object.

**Exceptions**

If no node with the specified label exists:

```
OdbError: Invalid node label
```

### 34.15.7 assignSection(...)

This method is used to assign a section to a region on an instance.

**Required arguments**

*region*

An [OdbSet](pt01ch34pyo23.md)                              specifying a region on an instance.

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

If the element set is not from the current instance:

```
OdbError: Section assignment requires element set from this part instance.
```

### 34.15.8 AnalyticRigidSurf2DPlanar(...)

This method is used to define a two-dimensional [AnalyticSurface](pt01ch34pyo02.md)                     object on the instance.

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

If [OdbPart](pt01ch34pyo19.md)                           associated with the part instance is of type THREE_D:

```
OdbError: 2D-Planar Analytic Rigid Surface can be defined only if the instance is of type                             TWO_D_PLANAR                            or                             AXISYMMETRIC.                         
```

### 34.15.9 AnalyticRigidSurfExtrude(...)

This method is used to define a three-dimensional cylindrical [AnalyticSurface](pt01ch34pyo02.md)                     on the instance.

**Required arguments**

*name*

The name of the analytic surface.

*profile*

A sequence of [AnalyticSurfaceSegment](pt01ch34pyo03.md)                              objects or an [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md)                              object.

**Optional arguments**

*filletRadius*

A Double specifying the radius of curvature to smooth discontinuities between adjoining segments. The default value is 0.0.

*localCoordData*

A sequence of sequences of Floats specifying the global coordinates of points used to define the local coordinate system.

**Return value**

None

**Exceptions**

If [OdbPart](pt01ch34pyo19.md)                           associated with the part instance is not of type THREE_D:

```
OdbError:  Analytic Rigid Surface of type                             CYLINDER                            can be defined only if the instance is of type                             THREE_D.                         
```

### 34.15.10 AnalyticRigidSurfRevolve(...)

This method is used to define a three-dimensional [AnalyticSurface](pt01ch34pyo02.md)                     of revolution on the instance.

**Required arguments**

*name*

The name of the analytic surface.

*profile*

A sequence of [AnalyticSurfaceSegment](pt01ch34pyo03.md)                              objects or an [OdbSequenceAnalyticSurfaceSegment](pt01ch34pyo22.md)                              object.

**Optional arguments**

*filletRadius*

A Double specifying the radius of curvature to smooth discontinuities between adjoining segments. The default value is 0.0.

*localCoordData*

A sequence of sequences of Floats specifying the global coordinates of points used to define the local coordinate system.

**Return value**

None

**Exceptions**

If [OdbPart](pt01ch34pyo19.md)                           associated with the part instance is not of type THREE_D:

```
OdbError:  Analytic Rigid Surface of type                             REVOLUTION                            can be defined only if the instance is of type                             THREE_D.                         
```

### 34.15.11 RigidBody(...)

This method defines an [OdbRigidBody](pt01ch34pyo21.md)                     on the instance.

**Required argument**

*referenceNode*

An [OdbSet](pt01ch34pyo23.md)                              specifying the reference node assigned to the rigid body.

**Optional arguments**

*position*

A symbolic constant specify if the location of the reference node is to be defined by the user. Possible values are INPUT, and CENTER_OF_MASS. The default value is INPUT.

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

### 34.15.12 getNodeFromLabel(...)

This method is used to retrieved a node with a specific label from an instance object.

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

### 34.15.13 getNodeFromLabel(...)

This method is used to retrieved a node with a specific label from an instance object.

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

### 34.15.14 Members

The OdbInstance object can have the following members:

*name*

A String specifying the instance name.

*type*

A SymbolicConstant specifying the type of the [Part](pt01ch37pyo01.md)                  object. Only a value of DEFORMABLE_BODY                  is currently supported.

*embeddedSpace*

A SymbolicConstant specifying the dimensionality of the [Part](pt01ch37pyo01.md)                  object.                 Possible values are THREE_D, TWO_D_PLANAR, AXISYMMETRIC, and UNKNOWN_DIMENSION.

*resultState*

A SymbolicConstant specifying the state of the Instance as modified by the analysis. This member is only present if the Instance is part of the RootAssemblyState tree. Possible values are:
- PROPAGATED, specifying that the value is the same as the previous frame or the original rootAssembly.
- MODIFIED, specifying that the geometry of the instance has been changed at this frame.

The default value is PROPAGATED.

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

*rigidBodies*

An [OdbRigidBodyArray](pt01ch34pyo21.md) object.

*beamOrientations*

A [BeamOrientationArray](pt01ch34pyo04.md) object.

*materialOrientations*

A [MaterialOrientationArray](pt01ch44pyo04.md) object.

*rebarOrientations*

A [RebarOrientationArray](pt01ch34pyo25.md) object.

*analyticSurface*

An [AnalyticSurface](pt01ch34pyo02.md) object specifying analytic Surface defined on the instance.




