# 48.2 ConstrainedSketchConstraint object







The ConstrainedSketchConstraint               object stores the constraints associated with a sketch.

**Access**

```
import sketch
mdb.models[*name*].sketches[*name*].constraints[*i*]
```

### 48.2.1 CoincidentConstraint(...)

This method creates a coincident constraint. This constraint applies to two vertices, to a vertex and a [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     object, or to two [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects of the same type and constrains them to be coincident.

**Path**

```
mdb.models[*name*].sketches[*name*].CoincidentConstraint
```

**Required arguments**

*entity1*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object or a [Vertex](pt01ch07pyo15.md)                              object specifying the first object.

*entity2*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object or a [Vertex](pt01ch07pyo15.md)                              object specifying the second object.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.2 ConcentricConstraint(...)

This method creates a concentric constraint. This constraint applies to any combination of circles, arcs, ellipses, and points and constrains them to be concentric. A concentric constraint implies that the center of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects coincide.

**Path**

```
mdb.models[*name*].sketches[*name*].ConcentricConstraint
```

**Required arguments**

*entity1*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the first arc, circle, ellipse, or sketch vertex.

*entity2*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the second arc, circle, ellipse, or sketch vertex.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.3 EqualLengthConstraint(...)

This method creates an equal length constraint. This constraint applies to lines and constrains them such that their lengths are equal.

**Path**

```
mdb.models[*name*].sketches[*name*].EqualLengthConstraint
```

**Required arguments**

*entity1*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the first line.

*entity2*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the second line.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.4 EqualRadiusConstraint(...)

This method creates an equal radius constraint. This constraint applies to circles and arcs and constrains them such that their radii are equal.

**Path**

```
mdb.models[*name*].sketches[*name*].EqualRadiusConstraint
```

**Required arguments**

*entity1*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the first arc or circle.

*entity2*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              specifying the second arc or circle.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.5 FixedConstraint(...)

This method creates a fixed constraint. This constraint applies to a [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     object or a [Vertex](pt01ch07pyo15.md)                     object and constrains them to be fixed in space. Both the location and the shape of the sketch geometry is fixed.

**Path**

```
mdb.models[*name*].sketches[*name*].FixedConstraint
```

**Required argument**

*entity*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object or a [Vertex](pt01ch07pyo15.md)                              object specifying the item to fix in space.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.6 HorizontalConstraint(...)

This method creates a horizontal constraint. This constraint applies to a line and constrains it to be horizontal.

**Path**

```
mdb.models[*name*].sketches[*name*].HorizontalConstraint
```

**Required argument**

*entity*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the line to constrain.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.7 VerticalConstraint(...)

This method creates a vertical constraint. This constraint applies to a line and constrains it to be vertical.

**Path**

```
mdb.models[*name*].sketches[*name*].VerticalConstraint
```

**Required argument**

*entity*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the line to constrain.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.8 ParallelConstraint(...)

This method creates a parallel constraint. This constraint applies to lines and constrains them to be parallel.

**Path**

```
mdb.models[*name*].sketches[*name*].ParallelConstraint
```

**Required arguments**

*entity1*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the first line.

*entity2*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the second line.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.9 PerpendicularConstraint(...)

This method creates a perpendicular constraint. This constraint applies to different types of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects and constrains them to be perpendicular to each other.

**Path**

```
mdb.models[*name*].sketches[*name*].PerpendicularConstraint
```

**Required arguments**

*entity1*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the first object.

*entity2*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the second object.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.10 EqualDistanceConstraint(...)

This method creates an equal distance constraint. This constraint can be applied between a midpoint [Vertex](pt01ch07pyo15.md)                     object and any other two [Vertex](pt01ch07pyo15.md)                     objects or between a midpoint [Vertex](pt01ch07pyo15.md)                     object and two [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects that are lines. The equal distance constraint forces the midpoint vertex to remain at an equal distance from the two other vertices or lines.

**Path**

```
mdb.models[*name*].sketches[*name*].EqualDistanceConstraint
```

**Required arguments**

*entity1*

A[ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the first line or [Vertex](pt01ch07pyo15.md)                              object.

*entity2*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the second line or [Vertex](pt01ch07pyo15.md)                              object.

*midpoint*

A [Vertex](pt01ch07pyo15.md)                              object specifying the vertex that will be positioned an equal distance from *entity1*                              and *entity2*.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.11 TangentConstraint(...)

This method creates a tangent constraint. This constraint applies to different types of [ConstrainedSketchGeometry](pt01ch48pyo05.md)                     objects and constrains them to remain tangential.

**Path**

```
mdb.models[*name*].sketches[*name*].TangentConstraint
```

**Required arguments**

*entity1*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the first object.

*entity2*

A [ConstrainedSketchGeometry](pt01ch48pyo05.md)                              object specifying the second object.

**Optional arguments**

None.

**Return value**

A ConstrainedSketchConstraint object.

**Exceptions**

None.

### 48.2.12 Members

The ConstrainedSketchConstraint object has no members.




