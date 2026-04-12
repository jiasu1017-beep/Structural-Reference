# 61.2 AnalyticSurface object







The AnalyticSurface object is a geometric surface that can be described with straight and/or curved line segments.

**Access**

```
odb.parts()[*name*].analyticSurface()
odb.rootAssembly().instances()[*name*].analyticSurface()
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.analyticSurface()
```

### 61.2.1 Members

The AnalyticSurface object has the following members:

**Prototype**

```
odb_String name() const;
odb_String type() const;
double filletRadius() const;
odb_SequenceSequenceFloat localCoordData() const;
odb_SequenceAnalyticSurfaceSegment segments() const;
```

*name*

An odb_String specifying the name of the analytic surface.

*type*

An odb_Enum::odb_typeEnum specifying the type of AnalyticSurface object. Possible values are odb_Enum::SEGMENTS, odb_Enum::CYLINDER, and odb_Enum::REVOLUTION.

*filletRadius*

A Double specifying radius of curvature to smooth discontinuities between adjoining segments. The default value is 0.0.

*segments*

An [OdbSequenceAnalyticSurfaceSegment](pt02ch61pyo23.md) object specifying the profile associated with the surface.

*localCoordData*

An odb_SequenceSequenceFloat specifying the global coordinates of points representing the local coordinate system, if used.




