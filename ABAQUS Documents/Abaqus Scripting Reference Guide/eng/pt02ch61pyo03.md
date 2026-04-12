# 61.3 AnalyticSurfaceSegment object







An individual segment of the analytic surface.

**Access**

```
odb.parts()[*name*].analyticSurface().segments(*i*)
odb.rootAssembly().instances()[*name*].analyticSurface().segments(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.analyticSurface().segments(*i*)
```

### 61.3.1 Members

The AnalyticSurfaceSegment object has the following members:

**Prototype**

```
odb_String type() const;
odb_SequenceSequenceFloat data() const;
```

*type*

An odb_Enum::odb_typeEnum specifying the type of AnalyticSurfaceSegment. Possible values are odb_Enum::START, odb_Enum::LINE, odb_Enum::CIRCLE, and odb_Enum::PARABOLA.

*data*

An odb_SequenceSequenceFloat specifying the coordinates of point/s representing the segment of the [AnalyticSurface](pt02ch61pyo02.md) object. If *type*=odb_Enum::CIRCLE, the first row contains coordinates of the end point and the               second row contains coordinates of the center point. If *type*=odb_Enum::PARABOLA, the first row contains coordinates of the middle point and the               second row contains coordinates of the end point. If *type*=odb_Enum::START or *type*=odb_Enum::LINE, a single row contains coordinates of the start/end point. 




