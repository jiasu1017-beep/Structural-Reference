# 61.26 RebarOrientation object







The RebarOrientation object represents the orientation of the rebar reference.

**Access**

```
odb.parts()[*name*].rebarOrientations(*i*)
odb.rootAssembly().instances()[*name*].rebarOrientations(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.rebarOrientations(*i*)
```

### 61.26.1 Members

The RebarOrientation object can have the following members:

**Prototype**

```
odb_Set region() const;
odb_DatumCsys csys() const;
odb_Enum::odb_AxisEnum axis() const;
float angle() const;

```

*axis*

An odb_Enum::odb_AxisEnum specifying the axis of a cylindrical or spherical datum coordinate system about which an additional rotation is applied. Possible values are odb_Enum::AXIS_1, odb_Enum::AXIS_2, and odb_Enum::AXIS_3.

*angle*

A Float specifying the angle of the additional rotation.

*region*

An [OdbSet](pt02ch61pyo24.md) object specifying a region for which the rebar orientation is defined.

*csys*

An [OdbDatumCsys](pt02ch61pyo14.md) object specifying a datum coordinates system.




