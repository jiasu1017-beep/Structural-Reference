# 34.1 Odb object







The Odb               object is the in-memory representation of an output database (ODB) file.

**Access**

```
import odbAccess
session.odbs[*name*]
```

### 34.1.1 Odb(...)

This method creates a new Odb                     object.

**Path**

```
session.Odb
```

**Required argument**

*name*

A String specifying the repository key.

**Optional arguments**

*analysisTitle*

A String specifying the title of the output database. The default value is an empty string.

*description*

A String specifying the description of the output database. The default value is an empty string.

*path*

A String specifying the path to the file where the new output database (`.odb`                     ) file will be written.                    The default value is an empty string.

**Return value**

An Odb object.

**Exceptions**

None.

### 34.1.2 close()

This method closes an output database.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 34.1.3 getFrame(...)

This method returns the frame at the specified time, frequency, or mode. It will not interpolate values between frames. The method is not applicable to an Odb                     object containing steps with different domains or to an Odb                     object containing a step with load case specific data.

**Required argument**

*frameValue*

A Double specifying the value at which the frame is required. *frameValue*                              can be the total time or frequency.

**Optional argument**

*match*

A SymbolicConstant specifying which frame to return if there is no frame at the exact frame value. Possible values are CLOSEST, BEFORE, AFTER, and EXACT. The default value is CLOSEST.

When *match*=CLOSEST, Abaqus returns the closest frame. If the frame value requested is exactly halfway between two frames, Abaqus returns the frame after the value.

When *match*=EXACT, Abaqus raises an exception if the exact frame value does not exist.

**Return value**

An [OdbFrame](pt01ch34pyo14.md)                     object.

**Exceptions**

If the exact frame is not found:

```
OdbError: Frame not found.
```

### 34.1.4 save()

This method saves output to an output database (`.odb`                     ) file.

**Arguments**

None.

**Return value**

None

**Exceptions**

OdbError

```
Database save failed. The database was opened as read-only. Modification of data is not permitted.
```

### 34.1.5 update()

This method is used to update an Odb                     object in memory while an Abaqus analysis writes data to the associated output database. `update`                     checks if additional steps have been written to the output database since it was opened or last updated. If additional steps have been written to the output database, `update`                     adds them to the Odb                     object.

**Arguments**

None.

**Return value**

A Boolean specifying whether additional steps or frames were added to the Odb                     object.

**Exceptions**

None.

### 34.1.6 Members

The Odb object has members with the same names and descriptions as the arguments to the [Odb](pt01ch34pyo01.md#ker-odb-odb-pyc) method.

In addition, the Odb object can have the following members:

*isReadOnly*

A Boolean specifying whether the output database was opened with read-only access.

*amplitudes*

A repository of [Amplitude](pt01ch03pyo01.md) objects.

*filters*

A repository of [Filter](pt01ch22pyo01.md) objects.

*rootAssembly*

An [OdbAssembly](pt01ch34pyo12.md) object.

*jobData*

A [JobData](pt01ch34pyo11.md) object.

*parts*

A repository of [OdbPart](pt01ch34pyo19.md) objects.

*materials*

A repository of [Material](pt01ch29pyo01.md) objects.

*steps*

A repository of [OdbStep](pt01ch34pyo24.md) objects.

*sections*

A repository of [Section](pt01ch46pyo01.md) objects.

*sectionCategories*

A repository of [SectionCategory](pt01ch34pyo27.md) objects.

*sectorDefinition*

A [SectorDefinition](pt01ch34pyo29.md) object.

*userData*

A [UserData](pt01ch34pyo30.md) object.

*customData*

A [RepositorySupport](pt01ch14pyo02.md) object.

*profiles*

A repository of [Profile](pt01ch08pyo01.md) objects.




