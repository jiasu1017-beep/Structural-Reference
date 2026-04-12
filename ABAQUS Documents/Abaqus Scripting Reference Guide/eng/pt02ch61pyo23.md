# 61.23 OdbSequenceAnalyticSurfaceSegment object







A sequence of [AnalyticSurfaceSegment](pt02ch61pyo03.md) describing an analytic surface profile.

**Access**

```
odb.parts()[*name*].analyticSurface().segments()
odb.rootAssembly().instances()[*name*].analyticSurface().segments()
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.analyticSurface().segments()
```

### 61.23.1 Start(...)

This method adds a [AnalyticSurfaceSegment](pt02ch61pyo03.md) describing the first segment of the surface profile.

**Prototype**

```
void
Start(const odb_SequenceFloat& origin);
```

**Required argument**

*origin*

An odb_SequenceFloat specifying the coordinates of start point.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.23.2 Line(...)

This method adds a [AnalyticSurfaceSegment](pt02ch61pyo03.md) describing the line segment of the surface profile.

**Prototype**

```
void
Line(const odb_SequenceFloat& endPoint);
```

**Required argument**

*endPoint*

An odb_SequenceFloat specifying the coordinates of end point.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.23.3 Circle(...)

This method adds a [AnalyticSurfaceSegment](pt02ch61pyo03.md) describing a circular segment of the surface profile.

**Prototype**

```
void
Circle(const odb_SequenceFloat& center,
       const odb_SequenceFloat& endPoint);
```

**Required arguments**

*center*

An odb_SequenceFloat specifying the coordinates of center of the circular segment.

*endPoint*

An odb_SequenceFloat specifying the coordinates of end point of the circular segment.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.23.4 Parabola(...)

This method adds a [AnalyticSurfaceSegment](pt02ch61pyo03.md) describing a parabolic segment of the surface profile.

**Prototype**

```
void
Parabola(const odb_SequenceFloat& middlePoint,
         const odb_SequenceFloat& endPoint);
```

**Required arguments**

*middlePoint*

An odb_SequenceFloat specifying the coordinates of middle point of the parabolic segment.

*endPoint*

An odb_SequenceFloat specifying the coordinates of end point of the parabolic segment.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.23.5 Members

The OdbSequenceAnalyticSurfaceSegment object has no members.




