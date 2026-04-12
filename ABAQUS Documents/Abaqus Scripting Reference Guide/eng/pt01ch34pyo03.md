# 34.3 AnalyticSurfaceSegment object







An individual segment of the analytic surface.

**Access**

```
import odbAccess
session.odbs[*name*].parts[*name*].analyticSurface.segments[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].analyticSurface\
.segments[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.analyticSurface.segments[*i*]
```

### 34.3.1 AnalyticSurfaceSegment(...)

This method creates an AnalyticSurfaceSegment object.

**Path**

```
odbAccess.AnalyticSurfaceSegment
```

**Required arguments**

*type*

A SymbolicConstant specifying the type of AnalyticSurfaceSegment. Possible values are START, LINE, CIRCLE, and PARABOLA.

*data*

A sequence of sequences of Floats specifying the coordinates of point/s representing the segment of the [AnalyticSurface](pt01ch34pyo02.md) object. If *type*=CIRCLE, the first row contains coordinates of the end point and the               second row contains coordinates of the center point. If *type*=PARABOLA, the first row contains coordinates of the middle point and the               second row contains coordinates of the end point. If *type*=START or *type*=LINE, a single row contains coordinates of the start/end point. 

**Optional arguments**

None.

**Return value**

An AnalyticSurfaceSegment object.

**Exceptions**

None.

### 34.3.2 Members

The AnalyticSurfaceSegment object has members with the same names and descriptions as the arguments to the [AnalyticSurfaceSegment](pt01ch34pyo03.md#ker-analyticsurfacesegment-analyticsurfacesegment-pyc) method.




