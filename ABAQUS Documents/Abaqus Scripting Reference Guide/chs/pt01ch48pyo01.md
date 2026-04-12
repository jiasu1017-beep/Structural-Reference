# 48.1 ConstrainedSketch object







A ConstrainedSketch               object contains the entities that are used to create a sketch. The objects include [ConstrainedSketchGeometry](pt01ch48pyo05.md)               objects contained in the Geometry Repository, such as Line, Arc, and Spline. Vertex, Dimension, Constraint, and Parameter objects are contained in their respective repositories.

**Access**

```
import sketch
mdb.models[*name*].sketches[*name*]
```

### 48.1.1 ConstrainedSketch(...)

This method creates a ConstrainedSketch                     object. If the sketch cannot be created, the method returns `None`.

**Path**

```
mdb.models[*name*].ConstrainedSketch
```

**Required arguments**

*name*

A String specifying the repository key.

*sheetSize*

A Float specifying the sheet size.

**Optional arguments**

*gridSpacing*

A Float specifying the spacing between gridlines. Possible values are Floats ![](../graphics/ker_eqn00060.gif)                              0. The default value is approximately 2 percent of *sheetSize*.

*transform*

A sequence of sequences of Floats specifying the three-dimensional orientation of the sketch. The sequence is a 3  4 transformation matrix specifying the axis of rotation and the translation vector. Possible values are any Floats.

The default value for the axis of rotation is the identity matrix

```
(1.0, 0.0, 0.0),  (0.0, 1.0, 0.0),  (0.0, 0.0, 1.0)
```
                              The default value for the translation vector is
```
(0.0, 0.0, 0.0)
```
                              The default values position the sketch on the *X–Y* plane centered at the origin.

**Return value**

A ConstrainedSketch object.

**Exceptions**

None.

### 48.1.2 ConstrainedSketch(...)

This method copies one ConstrainedSketch                     object to a new ConstrainedSketch                     object.

**Note:**If the name of the sketch to be copied to is `__edit__`, Abaqus creates an exact copy that contains both reference geometry and a non-identity transform matrix. Otherwise, the `Sketch`                           copy constructor strips the reference geometry from the copied sketch and sets the transform matrix to identity, creating a standalone copy.

**Path**

```
mdb.models[*name*].ConstrainedSketch
```

**Required arguments**

*name*

A String specifying the repository key.

*objectToCopy*

A ConstrainedSketch                              object to be copied.

**Optional arguments**

None.

**Return value**

A ConstrainedSketch object.

**Exceptions**

InvalidNameError.

### 48.1.3 ConstrainedSketchFromGeometryFile(...)

This method creates a ConstrainedSketch                     object and places it in the `sketches`                     repository.

**Path**

```
mdb.models[*name*].ConstrainedSketchFromGeometryFile
```

**Required arguments**

*name*

A String specifying the repository key.

*geometryFile*

An [AcisFile](pt01ch37pyo03.md)                              object specifying a file containing geometry. The geometry in the file is converted to two-dimensional sketch geometry in the *X–Y* plane.

**Optional arguments**

None.

**Return value**

A ConstrainedSketch                     object.

**Exceptions**

InvalidNameError.

### 48.1.4 print()

This method prints the following statistics about a sketch:
- The sketch Id (a positive integer).
- The number of geometry curves (the number of [ConstrainedSketchGeometry](pt01ch48pyo05.md) objects).
- The number of dimensions (the number of [ConstrainedSketchDimension](pt01ch48pyo03.md) objects).
- The number of vertices (the number of [ConstrainedSketchVertex](pt01ch48pyo10.md) objects).

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.5 assignCenterline(...)

This method indicates the construction line that will be used as a centerline for revolved features.

**Required argument**

*line*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying a construction line that indicates the centerline of revolved features.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.6 assignCenterOfTwist(...)

This method indicates the isolated point that will be used as the center of twist when an extruded feature is created with twist.

**Required argument**

*point*

A [ConstrainedSketchVertex](pt01ch48pyo10.md)                              object specifying an isolated point that indicates the center of twist for extruded features that use a twist angle.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.7 autoDimension(...)

This method applies dimensions to the selected [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects in an effort to make the ConstrainedSketch                     well defined.

**Required argument**

*objectList*

A sequence specifying the [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects to dimension.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.8 autoTrimCurve(...)

This method automatically trims a selected [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     object at the specified location. If the object does not intersect other [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects, the entire selected object will be deleted.

**Required arguments**

*curve1*

The [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object to be trimmed.

*point1*

A pair of Floats specifying the location on [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              where the trimming should be applied. *point1*                              and *parameter1*                              are mutually exclusive.

*parameter1*

A Float specifying the parameter location on the [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              where the trimming should be applied. *point1*                              and *parameter1*                              are mutually exclusive.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.9 breakCurve(...)

This method breaks a specified [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     object (*curve1*) using another specified [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     object (*curve2*). If the selected [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects intersect, then only *curve1*                     will be broken; *curve2*                     is not affected by the operation. The location for the break is determined by the specified point values.

**Required arguments**

*curve1*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the object to be broken.

*point1*

A pair of Floats specifying the location on *curve1*                              near where the break should be applied.

*curve2*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying where *curve1*                              should be broken.

*point2*

A pair of Floats specifying the location on *curve2*                              near where *curve1*                              should be broken.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.10 copyMirror(...)

This method creates copies of the given [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects, mirrors them about a selected line, and inserts them into the appropriate repositories of the ConstrainedSketch                     object.

**Required arguments**

*mirrorLine*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the line about which Abaqus will mirror the sketch.

*objectList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects specifying the sketch to be copied and mirrored.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.11 copyMove(...)

This method creates copies of the given [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects, moves them from their original position, and inserts them into the appropriate repositories of the ConstrainedSketch                     object.

**Required arguments**

*vector*

A sequence of two Floats specifying the translation vector.

*objectList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects to be copied and moved.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.12 copyRotate(...)

This method creates copies of the given [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects, rotates them, and inserts them into the appropriate repositories of the ConstrainedSketch                     object.

**Required arguments**

*centerPoint*

A pair of Floats specifying the center of rotation.

*angle*

A Float specifying the angle of rotation in degrees.

*objectList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects to be copied and moved.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.13 copyScale(...)

This method creates copies of the given [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects, scales them by the specified value about a selected point, and inserts them into the appropriate repositories of the ConstrainedSketch                     object.

**Required arguments**

*scaleValue*

A Float specifying the value for scaling.

*scaleCenter*

A pair of Floats specifying the center of scaling.

*objectList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects to be copied and scaled.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.14 delete(...)

This method deletes the given [ConstrainedSketchGeometry](pt01ch48pyo05.md), [ConstrainedSketchDimension](pt01ch48pyo03.md), or [ConstrainedSketchConstraint](pt01ch48pyo02.md)                     objects.

**Required argument**

*objectList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md), [ConstrainedSketchDimension](pt01ch48pyo03.md), or [ConstrainedSketchConstraint](pt01ch48pyo02.md)                              objects to be deleted.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.15 deleteParameter(...)

The command deletes a specified parameter.

**Required argument**

*name*

A String specifying the name of the parameter to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.16 dragEntity(...)

This method drags a specified [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     or [ConstrainedSketchVertex](pt01ch48pyo10.md)                     object to a specific location.

**Required arguments**

*entity*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              or [ConstrainedSketchVertex](pt01ch48pyo10.md)                              object specifying the object to drag.

*points*

A sequence of sequences of three Floats specifying a sequence of points along which to drag the entity. The order of points in the sequence defines a path that determines the solution.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.17 linearPattern(...)

This method copies [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects in a linear pattern along one or two directions. This method also copies any associated dimension or constraint objects that exist between the given objects.

**Required arguments**

*number1*

An Integer specifying the total number of copies, including the original objects, that appear along the first direction in the pattern. Possible values are 1 ![](../graphics/ker_eqn00013.gif)                               *number1*                               ![](../graphics/ker_eqn00013.gif)                              1000.

*spacing1*

A Float specifying the spacing between copies along the first direction in the pattern. Possible values are 0.0 ![](../graphics/ker_eqn00419.gif)                               *spacing1*                              .

*angle1*

A Float specifying the angle in degrees of the first direction in the pattern. Possible values are –360.0 ![](../graphics/ker_eqn00013.gif)                               *angle1*                               ![](../graphics/ker_eqn00013.gif)                              360.0.

**Optional arguments**

*vertexList*

A sequence of [ConstrainedSketchVertex](pt01ch48pyo10.md)                              objects to copy.

*geomList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects to copy.

*number2*

An integer specifying the total number of copies, including the original objects, that appear along the second direction in the pattern. Possible values are 1 ![](../graphics/ker_eqn00013.gif)                               *number2*                               ![](../graphics/ker_eqn00013.gif)                              1000. The default value is 1. The value of either *number1*                              or *number2*                              must be greater than one.

*spacing2*

A Float specifying the spacing between copies along the first direction in the pattern. Possible values are 0.0 ![](../graphics/ker_eqn00419.gif)                               *spacing2*. The default value is *spacing1*.

*angle2*

A Float specifying the angle in degrees of the first direction in the pattern. Possible values are –360.0 ![](../graphics/ker_eqn00013.gif)                               *angle2*                               ![](../graphics/ker_eqn00013.gif)                              360.0. The default value is 90 beyond the value of *angle1*.

**Return value**

None

**Exceptions**

AbaqusException

```
Number must be greater than 1 for at least one direction
```

### 48.1.18 mergeVertices(...)

This method merges the [ConstrainedSketchVertex](pt01ch48pyo10.md)                     objects that lie within the specified distance of each other. If only one [ConstrainedSketchVertex](pt01ch48pyo10.md)                     object is selected, it will merge all [ConstrainedSketchVertex](pt01ch48pyo10.md)                     objects that lie within the specified distance of that vertex. If more than one vertex is selected, the search will be restricted to only the selected [ConstrainedSketchVertex](pt01ch48pyo10.md)                     objects.

**Required arguments**

*value*

A Float specifying the search radius.

*vertexList*

A sequence of [ConstrainedSketchVertex](pt01ch48pyo10.md)                              objects to be merged.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.19 move(...)

This method translates the given [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects by the given vector.

**Required arguments**

*vector*

A sequence of two Floats specifying the translation vector.

*objectList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects specifying the objects to be translated.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.20 offset(...)

This method creates copies of the selected [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects, offsets them by the specified distance in the specified direction, and inserts them into the ConstrainedSketch                     object's appropriate repositories. If connected objects are selected, trim or extend is carried out to complete the offset.

**Required arguments**

*distance*

A Float specifying the distance to be offset.

*objectList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects to be copied and offset.

*side*

A SymbolicConstant specifying which side the offset should occur. Possible values are LEFT                              and RIGHT.

**Optional argument**

*filletCorners*

A Boolean specifying whether the corners need to be rounded instead of being extended.

**Return value**

None

**Exceptions**

None.

### 48.1.21 radialPattern(...)

This method copies [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects in a radial pattern about a specified center point.

**Required arguments**

*number*

An Int specifying the total number of copies, including the original objects, that appear in the radial pattern. Possible values are 2 ![](../graphics/ker_eqn00013.gif)                               *number2*                               ![](../graphics/ker_eqn00013.gif)                              1000.

*totalAngle*

A Float specifying the total angle in degrees between the first and  last instance in the pattern. A positive angle corresponds to a  counter-clockwise direction. The values 360 and -360 represent a special case where the pattern makes a full circle. In this case, because the copy would overlay the original, the copy is not placed at the last position. Possible values are –360.0 ![](../graphics/ker_eqn00013.gif)                               *totalAngle*                               ![](../graphics/ker_eqn00013.gif)                              360.0.

*centerPoint*

A pair of Floats specifying the center of the radial pattern.

**Optional arguments**

*vertexList*

A sequence of [ConstrainedSketchVertex](pt01ch48pyo10.md)                              objects to copy.

*geomList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects to copy.

**Return value**

None

**Exceptions**

None.

### 48.1.22 resetView()

This method resets the view to be perpendicular to the sketching plane.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.23 rectangle(...)

This method creates four lines that form a rectangle with diagonal corners defined by the given points and inserts them into the `geometry`                     repository of the ConstrainedSketch                     object.

**Required arguments**

*point1*

A pair of Floats specifying the first corner of the rectangle.

*point2*

A pair of Floats specifying the second corner of the rectangle.

**Optional arguments**

None.

**Return value**

An Int specifying the success or failure of the method. A value of 0 indicates failure.

**Exceptions**

None.

### 48.1.24 removeGapsAndOverlaps(...)

This method removes gaps and overlaps between sketch geometries specified by the user. This method is particularly useful when cleaning up imported sketches

**Required arguments**

*tolerance*

A float value which specifies the largest size of the gap or overlap between entities that is to be removed. Typically this value is small and is used to close gaps and overlaps which may not exist in the originating program but exist in the sketch because of mismatched tolerances between the two programs.

*geomList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects where the gaps and overlaps are to be removed.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.25 repairShortEdges(...)

This method deletes the short edges specified, optionally selecting only those short edges whose lengths are smaller than the specified tolerance and healing the resultant gap in the sketch. This method is particularly useful in conjunction with `removeGapsAndOverlap`                     when cleaning up imported sketches.

**Required argument**

*geomList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects where the short edges are to be removed.

**Optional argument**

*tolerance*

A float value that is used to select and delete only those edges specified in *geomList*                              whose lengths are smaller than the given value. The default value is –1.0. This value implies that all edges specified in *geomList*                              will be removed and the sketch healed to remove gaps left by their removal.

**Return value**

None

**Exceptions**

None.

### 48.1.26 retrieveSketch(...)

This method copies all [ConstrainedSketchGeometry](pt01ch48pyo05.md), [ConstrainedSketchDimension](pt01ch48pyo03.md), [ConstrainedSketchConstraint](pt01ch48pyo02.md), and [ConstrainedSketchParameter](pt01ch48pyo09.md)                     objects from the specified ConstrainedSketch                     object. The new objects are added to the existing objects (if any). The objects in the specified ConstrainedSketch                     object are not modified by the retrieve operation.

**Required argument**

*sketch*

A ConstrainedSketch                              object specifying the object from which to copy.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.27 rotate(...)

This method rotates the given [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects by the given angle and about the given point.

**Required arguments**

*centerPoint*

A pair of Floats specifying the center of rotation.

*angle*

A Float specifying the angle of rotation in degrees.

*objectList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              specifying the objects to be rotated.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.28 scale(...)

This method scales the given [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects by the given scale factor and about the given point.

**Required arguments**

*scaleValue*

A Float specifying the value of scale.

*scaleCenter*

A pair of Floats specifying the center of scale.

*objectList*

A sequence of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              objects specifying the objects to be scaled.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.29 setPrimaryObject(...)

This method makes the ConstrainedSketch                     object the primary object in the current viewport. The sketch remains the primary object in the current viewport until an `unsetPrimaryobject`                     command is issued.

**Required argument**

*option*

A SymbolicConstant specifying how the sketch is displayed. Possible values are:
- STANDALONE: Indicates a new stand-alone sketch. The current viewport is cleared and is replaced by the stand-alone sketch. The view direction is set to ![](../graphics/ker_eqn00085.gif).
- SUPERIMPOSE: Indicates that the sketch is superimposed on the current viewport. The view direction is changed to be perpendicular to the sketch plane. The change is effected smoothly as an animated sequence of many small viewing steps.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.30 trimExtendCurve(...)

This method trims or extends a specified [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     object (*curve1*) using another specified [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     object (*curve2*). *curve2*                     is not affected by the operation. The location for the trim or extend is determined by the specified point values.

**Required arguments**

*curve1*

The [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the object to be trimmed or extended.

*point1*

A pair of Floats specifying the location on *curve1*                              where trim or extend should be applied.

*curve2*

The [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the object to which *curve1*                              is trimmed or extended. *curve2*                              is not trimmed or extended.

*point2*

A pair of Floats specifying the location on *curve2*                              near where *curve1*                              should be trimmed or extended.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.31 undo()

This method undoes the effects of the last ConstrainedSketch                     object method.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.32 unsetPrimaryObject()

This method removes the ConstrainedSketch                     object from the current viewport, reversing the effects of the `setPrimaryobject`                     command. If the *option*                     argument was set to SUPERIMPOSE, the viewport will be returned to the view orientation that was in place when the `setPrimaryobject`                     command was issued. If the *option*                     argument was set to STANDALONE, the viewport will be left empty.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 48.1.33 writeAcisFile(...)

This method exports the geometry of the sketch to a named file in ACIS format.

**Required argument**

*fileName*

A String specifying the file name.

**Optional argument**

*version*

A Float specifying the ACIS version. For example, the Float “12.0”                              corresponds to ACIS Version 12.0. The default value is the current version of ACIS.

**Return value**

None

**Exceptions**

InvalidNameError.

### 48.1.34 writeIgesFile(...)

This method exports the geometry of the sketch to a named file in IGES format.

**Required argument**

*filename*

A String specifying the file name.

**Optional argument**

*flavor*

A SymbolicConstant specifying a particular flavor of IGES to export. Possible values areSTANDARD, AUTOCAD, SOLIDWORKS, JAMA, and MSBO.

**Return value**

None

**Exceptions**

InvalidNameError.

### 48.1.35 Members

The ConstrainedSketch object can have the following members:

*constraints*

A repository of [ConstrainedSketchConstraint](pt01ch48pyo02.md) objects.

*dimensions*

A repository of [ConstrainedSketchDimension](pt01ch48pyo03.md) objects.

*geometry*

A [ConstrainedSketchGeometryArray](pt01ch48pyo05.md) object specifying the sketch geometry, such as lines, arcs, circles, and splines.

*parameters*

A repository of [ConstrainedSketchParameter](pt01ch48pyo09.md) objects specifying sketch parameters, which may be associated with dimensions.

*sketchOptions*

A [ConstrainedSketchOptions](pt01ch48pyo08.md) object specifying the sketch option settings.

*vertices*

A [ConstrainedSketchVertexArray](pt01ch48pyo10.md) object.

*imageOptions*

A [ConstrainedSketchImageOptions](pt01ch48pyo07.md) object.




