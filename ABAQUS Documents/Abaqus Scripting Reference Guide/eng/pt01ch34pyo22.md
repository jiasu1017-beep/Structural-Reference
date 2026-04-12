# 34.22 OdbSequenceAnalyticSurfaceSegment object







A sequence of [AnalyticSurfaceSegment](pt01ch34pyo03.md) describing an analytic surface profile.

**Access**

```
import odbAccess
session.odbs[*name*].parts[*name*].analyticSurface.segments
session.odbs[*name*].rootAssembly.instances[*name*].analyticSurface\
.segments
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.analyticSurface.segments
```

### 34.22.1 AnalyticSurfaceProfile()

This method creates a OdbSequenceAnalyticSurfaceSegment object.

**Path**

```
odbAccess.AnalyticSurfaceProfile
```

**Return value**

An OdbSequenceAnalyticSurfaceSegment object.

**Exceptions**

None.

### 34.22.2 Start(...)

This method adds a [AnalyticSurfaceSegment](pt01ch34pyo03.md) describing the first segment of the surface profile.

**Required argument**

*origin*

A sequence of Floats specifying the coordinates of start point.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 34.22.3 Line(...)

This method adds a [AnalyticSurfaceSegment](pt01ch34pyo03.md) describing the line segment of the surface profile.

**Required argument**

*endPoint*

A sequence of Floats specifying the coordinates of end point.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 34.22.4 Circle(...)

This method adds a [AnalyticSurfaceSegment](pt01ch34pyo03.md) describing a circular segment of the surface profile.

**Required arguments**

*center*

A sequence of Floats specifying the coordinates of center of the circular segment.

*endPoint*

A sequence of Floats specifying the coordinates of end point of the circular segment.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 34.22.5 Parabola(...)

This method adds a [AnalyticSurfaceSegment](pt01ch34pyo03.md) describing a parabolic segment of the surface profile.

**Required arguments**

*middlePoint*

A sequence of Floats specifying the coordinates of middle point of the parabolic segment.

*endPoint*

A sequence of Floats specifying the coordinates of end point of the parabolic segment.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 34.22.6 Members

The OdbSequenceAnalyticSurfaceSegment object has no members.




