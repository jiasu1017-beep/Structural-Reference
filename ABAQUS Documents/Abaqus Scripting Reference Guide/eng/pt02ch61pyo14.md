# 61.14 OdbDatumCsys object







The OdbDatumCsys object contains a coordinate system that can be stored in an output database. You can create the datum coordinate system in the Visualization module during an Abaqus/CAE session and save the datum coordinate system to the output database before you exit Abaqus/CAE. Alternatively, the analysis code can write the datum coordinate system to the output database. 

**Access**

```
odb.rootAssembly().datumCsyses()[*name*]
```

### 61.14.1 DatumCsysByThreePoints(...)

This method creates an OdbDatumCsys object using three points. A datum coordinate system created with this method results in a fixed system. 

**Path**

```
odb.rootAssembly().DatumCsysByThreePoints
```

**Prototype**

```
odb_DatumCsys&
DatumCsysByThreePoints(const odb_String& name,
                odb_Enum::odb_DatumCsysTypeEnum type,
                const odb_SequenceFloat& origin,
                const odb_SequenceFloat& point1,
                const odb_SequenceFloat& point2);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*type*

An odb_Enum::odb_DatumCsysTypeEnum specifying the type of coordinate system. Possible values are odb_Enum::CARTESIAN, odb_Enum::CYLINDRICAL, and odb_Enum::SPHERICAL.

*origin*

An odb_SequenceFloat specifying the coordinates of the origin of the datum coordinate system.

*point1*

An odb_SequenceFloat specifying the coordinates of a point on the local 1- or ![](../graphics/ker_eqn00052.gif)-axis.

*point2*

An odb_SequenceFloat specifying the coordinates of a point in the 1–2 or ![](../graphics/ker_eqn00052.gif)–![](../graphics/ker_eqn00053.gif) plane.

**Optional arguments**

None.

**Return value**

An OdbDatumCsys object.

**Exceptions**

None.

### 61.14.2 DatumCsysByThreeNodes(...)

This method creates an OdbDatumCsys object using the coordinates of three [OdbMeshNode](pt02ch61pyo19.md) objects. A datum coordinate system created with this method results in a system that follows the position of the three nodes. Results, such as those for displacement, are resolved into the orientation of the datum coordinate system without regard to the position of its origin. The last three arguments are given in the form of an [OdbMeshNode](pt02ch61pyo19.md) object.

**Path**

```
odb.rootAssembly().DatumCsysByThreeNodes
```

**Prototype**

```
odb_DatumCsys&
DatumCsysByThreeNodes(const odb_String& name,
                odb_Enum::odb_DatumCsysTypeEnum type,
                const odb_Node& origin,
                const odb_Node& point1,
                const odb_Node& point2);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*type*

An odb_Enum::odb_DatumCsysTypeEnum specifying the type of coordinate system. Possible values are odb_Enum::CARTESIAN, odb_Enum::CYLINDRICAL, and odb_Enum::SPHERICAL.

*origin*

An [OdbMeshNode](pt02ch61pyo19.md) object specifying a node at the origin of the datum coordinate system.

*point1*

An [OdbMeshNode](pt02ch61pyo19.md) object specifying a node on the local 1- or ![](../graphics/ker_eqn00052.gif)-axis.

*point2*

An [OdbMeshNode](pt02ch61pyo19.md) object specifying a node in the 1–2 or ![](../graphics/ker_eqn00052.gif)–![](../graphics/ker_eqn00053.gif) plane.

**Optional arguments**

None.

**Return value**

An OdbDatumCsys object.

**Exceptions**

None.

### 61.14.3 DatumCsys(...)

This method copies oneOdbDatumCsys object to a new OdbDatumCsys object.

**Path**

```
odb.rootAssembly().DatumCsys
```

**Prototype**

```
odb_DatumCsys&
DatumCsys(const odb_String& name,
          const odb_DatumCsys& datumCsys);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*datumCsys*

An OdbDatumCsys object specifying the object to be copied.

**Optional arguments**

None.

**Return value**

An OdbDatumCsys object.

**Exceptions**

None.

### 61.14.4 Members

The OdbDatumCsys object has the following members:

**Prototype**

```
odb_String name() const;
odb_Enum::odb_DatumCsysTypeEnum type() const;
const float* origin() const;
float origin(int index) const;
const float* xAxis() const;
float xAxis(int index) const;
const float* yAxis() const;
float yAxis(int index) const;
const float* zAxis() const;
float zAxis(int index) const;
```

*name*

An odb_String specifying the repository key.

*type*

An odb_Enum::odb_DatumCsysTypeEnum specifying the type of coordinate system. Possible values are odb_Enum::CARTESIAN, odb_Enum::CYLINDRICAL, and odb_Enum::SPHERICAL.

*origin*

An odb_SequenceFloat specifying the coordinates of the origin of the datum coordinate system.

*xAxis*

An odb_SequenceFloat specifying a point on the *X*-axis.

*yAxis*

An odb_SequenceFloat specifying a point on the *Y*-axis.

*zAxis*

An odb_SequenceFloat specifying a point on the *Z*-axis.




