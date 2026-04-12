# 61.1 Odb object







The Odb               object is the in-memory representation of an output database (ODB) file.

**Access**

```
odb
```

### 61.1.1 Odb(...)

This method creates a new Odb                     object.

**Path**

```
Odb
```

**Prototype**

```
odb_Odb&
Odb(const odb_String& name,
    const odb_String& analysisTitle,
    const odb_String& description,
    const odb_String& path);
```

**Required argument**

*name*

An odb_String specifying the repository key.

**Optional arguments**

*analysisTitle*

An odb_String specifying the title of the output database. The default value is an empty string.

*description*

An odb_String specifying the description of the output database. The default value is an empty string.

*path*

An odb_String specifying the path to the file where the new output database (`.odb`                     ) file will be written.                    The default value is an empty string.

**Return value**

An Odb object.

**Exceptions**

None.

### 61.1.2 close()

This method closes an output database.

**Prototype**

```
void
close();
```

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.1.3 getFrame(...)

This method returns the frame at the specified time, frequency, or mode. It will not interpolate values between frames. The method is not applicable to an Odb                     object containing steps with different domains or to an Odb                     object containing a step with load case specific data.

**Prototype**

```
odb_Frame
getFrame(double frameValue,
         odb_Enum::odb_MatchEnum match);
```

**Required argument**

*frameValue*

A Double specifying the value at which the frame is required. *frameValue*                              can be the total time or frequency.

**Optional argument**

*match*

An odb_Enum::odb_MatchEnum specifying which frame to return if there is no frame at the exact frame value. Possible values are odb_Enum::CLOSEST, odb_Enum::BEFORE, odb_Enum::AFTER, and odb_Enum::EXACT. The default value is odb_Enum::CLOSEST.

When *match*=odb_Enum::CLOSEST, Abaqus returns the closest frame. If the frame value requested is exactly halfway between two frames, Abaqus returns the frame after the value.

When *match*=odb_Enum::EXACT, Abaqus raises an exception if the exact frame value does not exist.

**Return value**

An [OdbFrame](pt02ch61pyo15.md)                     object.

**Exceptions**

If the exact frame is not found:

```
OdbError: Frame not found.
```

### 61.1.4 save()

This method saves output to an output database (`.odb`                     ) file.

**Prototype**

```
void
save();
```

**Arguments**

None.

**Return value**

None

**Exceptions**

OdbError

```
Database save failed. The database was opened as read-only. Modification of data is not permitted.
```

### 61.1.5 update()

This method is used to update an Odb                     object in memory while an Abaqus analysis writes data to the associated output database. `update`                     checks if additional steps have been written to the output database since it was opened or last updated. If additional steps have been written to the output database, `update`                     adds them to the Odb                     object.

**Prototype**

```
bool
update();
```

**Arguments**

None.

**Return value**

A Boolean specifying whether additional steps or frames were added to the Odb                     object.

**Exceptions**

None.

### 61.1.6 hasSectorDefinition()

This method checks whether or not a valid [SectorDefinition](pt02ch61pyo29.md)                     object, indicating a cyclic symmetry model, is present.

**Prototype**

```
bool
hasSectorDefinition();
```

**Arguments**

None.

**Return value**

A Boolean specifying whether a valid sector definition is available.

**Exceptions**

None.

### 61.1.7 Members

The Odb object has members with the same names and descriptions as the arguments to the [Odb](pt02ch61pyo01.md#ker-odb-odb-cpp) method.

In addition, the Odb object can have the following members:

**Prototype**

```
odb_String name() const;
               odb_String analysisTitle() const;
               odb_String description() const;
               odb_String path() const;
               bool isReadOnly() const;
               odb_Assembly& rootAssembly();
               odb_JobData jobData() const;
               odb_PartRepository& parts();
               odb_StepRepository& steps();
               odb_SectionCategoryRepository& sectionCategories();
               odb_SectorDefinition& sectorDefinition();
               odb_InteractionRepository& interactions();
               odb_InteractionPropertyRepository& interactionProperties();
               odb_ConstraintRepository& constraints();
```

*isReadOnly*

A Boolean specifying whether the output database was opened with read-only access.

*rootAssembly*

An [OdbAssembly](pt02ch61pyo13.md) object.

*jobData*

A [JobData](pt02ch61pyo12.md) object.

*parts*

A repository of [OdbPart](pt02ch61pyo20.md) objects.

*steps*

A repository of [OdbStep](pt02ch61pyo25.md) objects.

*sectionCategories*

A repository of [SectionCategory](pt02ch61pyo27.md) objects.

*sectorDefinition*

A [SectorDefinition](pt02ch61pyo29.md) object.

*userData*

A [UserData](pt02ch61pyo30.md) object.




