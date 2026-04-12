# 25.51 Model object







The following commands operate on Model objects. For more information about the Model object, see ["Model object," Section 33.1](pt01ch33pyo01.md).

**Access**

```
import interaction
```

### 25.51.1 contactDetection(...)

This method uses contact detection to create [SurfaceToSurfaceContactStd](pt01ch25pyo75.md), [SurfaceToSurfaceContactExp](pt01ch25pyo74.md), and [Tie](pt01ch13pyo10.md)                     objects.

**Required arguments**

None.

**Optional arguments**

*name*

A String specifying the prefix used to generate repository keys.  The default value is "CP-"

*createStepName*

A String specifying the name of the step in which the [SurfaceToSurfaceContactStd](pt01ch25pyo75.md), [SurfaceToSurfaceContactExp](pt01ch25pyo74.md), and [Tie](pt01ch13pyo10.md)                              objects are created.  The default value is "Initial."

*searchDomain*

A SymbolicConstant MODEL                              or a sequence of Strings specifying the names of instances to search. MODEL                              indicates the whole model is searched. The default value is MODEL.

*defaultType*

A SymbolicConstant specifying the default type of object to create.  Possible values are CONTACT, CONTACT_STANDARD, CONTACT_EXPLICIT, and TIE.  If CONTACT                              is used, the behavior is determined by the type of [Step](pt01ch49pyo01.md)                              in the model.  If an [ExplicitDynamicsStep](pt01ch49pyo11.md)                              or [TempDisplacementDynamicsStep](pt01ch49pyo31.md)                              exists, then [SurfaceToSurfaceContactExp](pt01ch25pyo74.md)                              is created by default.  Otherwise [SurfaceToSurfaceContactStd](pt01ch25pyo75.md)                              is created by default.  The default value is CONTACT.

*interactionProperty*

A String specifying the name of the [ContactProperty](pt01ch25pyo21.md)                              object associated with any interactions created.

*separationTolerance*

A Float specifying the maximum separation for considering two surfaces to be candidates for contact, where separation is the maximum distance between the points of closest approach on the two surfaces.  The default value is a function of the model.

*extendByAngle*

 None                              or a Float specifying the angle for extending surface definitions to include adjacent faces. The default value is 20.

*mergeWithinAngle*

 None                              or a Float specifying the angle for merging adjacent contact pairs which lie within the angle.  The default value is 20.

*searchSingleInstances*

A Boolean specifying whether to include surface pairs within a single instance.  The default value is OFF.

*nameEachSurfaceFound*

A Boolean specifying whether to assign a name to each surface found.  The default value is ON.

*createUnionOfMasterSurfaces*

A Boolean specifying whether to create a surface that is the union of all master surfaces found.  The default value is OFF.

*createUnionOfSlaveSurfaces*

A Boolean specifying whether to create a surface that is the union of all slave surfaces found.  The default value is OFF.

*createUnionOfMasterSlaveSurfaces*

A Boolean specifying whether to create a surface that is the union of all master and slave surfaces found.  The default value is OFF.

*includePlanar*

A Boolean specifying whether to include planar geometry.  The default value is ON.

*includeCylindricalSphericalToric*

A Boolean specifying whether to include cylindrical, spherical and toric geometry.  The default value is ON.

*includeSplineBased*

A Boolean specifying whether to include spline-based geometry.  The default value is ON.

*includeMeshSolid*

A Boolean specifying whether to include solid mesh entities.  The default value is ON.

*includeMeshShell*

A Boolean specifying whether to include shell mesh entities.  The default value is ON.

*includeMeshMembrane*

A Boolean specifying whether to include mesh membrane entities.  The default value is OFF.

*includeOverclosed*

A Boolean specifying whether to include overclosed pairs.  The default value is ON.

*includeNonOverlapping*

A Boolean specifying whether to include opposing geometry surfaces that do not overlap. The default value is OFF.

*meshedGeometrySearchTechnique*

A SymbolicConstant USE_GEOMETRY                              or USE_MESH                              specifying whether to locate pairs in meshed geometry using the geometric entities or mesh entities.  The default value is USE_GEOMETRY.

*useShellThickness*

A Boolean specifying whether to account for shell thickness and offset during contact detection. The default value is ON.

*surfaceSmoothing*

A SymbolicConstant specifying whether to use surface smoothing for geometric surfaces in [SurfaceToSurfaceContactStd](pt01ch25pyo75.md)                              interactions.  Possible values are NONE and AUTOMATIC. The default value isAUTOMATIC.

**Return value**

None

**Exceptions**

None.



