# 61.4 BeamOrientation object







The BeamOrientation object represents the direction of the first beam section axis ![](../graphics/ker_eqn00406.gif). Specifying the beam orientation using an additional node in the element connectivity list is not supported.

**Access**

```
odb.parts()[*name*].beamOrientations(*i*)
odb.rootAssembly().instances()[*name*].beamOrientations(*i*)
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*).instance()\
.beamOrientations(*i*)
```

### 61.4.1 Members

The BeamOrientation object can have the following members:

**Prototype**

```
odb_Set region() const;
odb_Enum::odb_OrientationMethodEnum method() const;
odb_SequenceFloat vector() const;
```

*method*

An odb_Enum::odb_OrientationMethodEnum specifying the orientation assignment method. Possible values are odb_Enum::N1_COSINES, odb_Enum::CSYS, and odb_Enum::VECT.

*region*

An [OdbSet](pt02ch61pyo24.md) object specifying a region for which the beam orientation is defined.

*vector*

An odb_SequenceFloat specifying direction cosines of the ![](../graphics/ker_eqn00406.gif)-direction of the beam cross-section.




