# 61.32 Top level commands







The Odb commands do the following: 
- Determine if an output database (`.odb`) file needs to be upgraded to the current release.
- Determine the extreme value for an output variable over a number of fields; for example, over a number of load cases.
- Open an existing output database file and create a new Odb object.
- Upgrade an output database file to the current release and write the upgraded output database to a new file.
- Fetch the active output database from inside a C++ user subroutine during an analysis run.
- Determine the actual subtype of a base Section, Profile, or Amplitude object.
- Cast a base Section, Profile, or Amplitude object to the proper subtype.

### 61.32.1 isUpgradeRequiredForOdb(...)

This method determines if an output database file needs to be upgraded to the current release. 

**Prototype**

```
bool isUpgradeRequiredForOdb(const odb_String& upgradeRequiredOdbPath);
```

**Required argument**

*upgradeRequiredOdbPath*

An odb_String specifying the path to an output database file to test. The test determines if the output database needs to be upgraded to the current release.

**Optional arguments**

None.

**Return value**

A Boolean indicating the result of the test. A value of True indicates that the output database needs to be upgraded to the current release.

**Exceptions**

None.

### 61.32.2 maxEnvelope(...)

Retrieve the maximum value of an output variable over a number of fields.

**Prototype**

```
odb_SequenceFieldOutput maxEnvelope(
    const odb_SequenceFieldOutput & inputFields);
odb_SequenceFieldOutput maxEnvelope(
    const odb_SequenceFieldOutput & inputFields,
    odb_Enum::odb_InvariantEnum invariant);
odb_SequenceFieldOutput maxEnvelope(
    const odb_SequenceFieldOutput & inputFields,
    const odb_String& componentLabel);
```

**Required arguments**

| Argument |
| --- |
| An odb_SequenceFieldoutput object containing all the fieldOutput objects from which the maximum value will be computed. |
| A SymbolicConstant specifying the invariant or component label to be used when comparing vectors or tensors. Possible values are - odb_Enum::MAGNITUDE - odb_Enum::MISES - odb_Enum::TRESCA - odb_Enum::PRESS - odb_Enum::INV3 - odb_Enum::MAX_PRINCIPAL - odb_Enum::MID_PRINCIPAL - odb_Enum::MIN_PRINCIPAL You must provide either this argument or the following argument if the field is a vector or tensor. |
| An odb_String specifying the component of the tensor or vector to be used for selecting the maximum value. |

**Optional arguments**

None.

**Return value**

An odb_SequenceFieldOutput object. The first fieldOutput object contains the maximum value. The second fieldOutput object contains the index of the field containing the maximum value. The index follows the order in which fields are positioned in the list of fieldOutput objects provided as the argument to the function.

**Exceptions**

OdbError

TypeError

```
This function takes no keyword arguments.
```

### 61.32.3 minEnvelope(...)

Retrieve the minimum value of an output variable over a number of fields.

**Prototype**

```
odb_SequenceFieldOutput minEnvelope(
    const odb_SequenceFieldOutput & inputFields);
odb_SequenceFieldOutput minEnvelope(
    const odb_SequenceFieldOutput & inputFields,
    odb_Enum::odb_InvariantEnum invariant);
odb_SequenceFieldOutput minEnvelope(
    const odb_SequenceFieldOutput & inputFields,
    const odb_String& componentLabel);
```

**Required arguments**

| Argument |
| --- |
| An odb_SequenceFieldoutput object containing all the fieldOutput objects from which the maximum value will be computed. |
| A SymbolicConstant specifying the invariant or component label to be used when comparing vectors or tensors. Possible values are - odb_Enum::MAGNITUDE - odb_Enum::MISES - odb_Enum::TRESCA - odb_Enum::PRESS - odb_Enum::INV3 - odb_Enum::MAX_PRINCIPAL - odb_Enum::MID_PRINCIPAL - odb_Enum::MIN_PRINCIPAL You must provide either this argument or the following argument if the field is a vector or tensor. |
| An odb_String specifying the component of the tensor or vector to be used for selecting the minimum value. |

**Optional arguments**

None.

**Return value**

An odb_SequenceFieldOutput object. The first fieldOutput object contains the minimum value. The second fieldOutput object contains the index of the field containing the minimum value. The index follows the order in which fields are positioned in the list of fieldOutput objects provided as the argument to the function.

**Exceptions**

OdbError

TypeError

```
This function takes no keyword arguments.
```

### 61.32.4 openOdb(...)

This method opens an existing output database (`.odb`) file and creates a new Odb object. 

**Prototype**

```
odb_Odb& openOdb(const odb_String& path);
```

**Required argument**

*path*

A odb_String specifying the path to an existing output database (`.odb`) file.

**Optional argument**

*readOnly*

A Boolean specifying whether the file will permit only read access or both read and write access. The initial value is False, indicating that both read and write access will be permitted.

*readInternalSets*

A Boolean specifying whether the file will permit access to sets specified as Internal on the database. The initial value is False, indicating that internal sets will not be read.

**Return value**

An Odb object.

**Exceptions**

If the output database was generated by a previous release of Abaqus and needs upgrading:

```
OdbError: The database is from a previous release of Abaqus. Run `abaqus upgrade `
```

```
`-job <*newFilename*> -odb <*oldFileName*>` to upgrade it.
```

If the output database was generated by a newer release of Abaqus, and the installation of Abaqus needs upgrading:

```
OdbError: Abaqus installation must be upgraded before this output database can be opened.
```

### 61.32.5 openOdb(...)

This method opens an existing output database (`.odb`) file and creates a new Odb object. 

**Prototype**

```
odb_Odb& openOdb(const odb_String& name,
const odb_String& path, bool readOnly);
```

**Required argument**

*name*

A odb_String specifying the repository key.

**Optional arguments**

*path*

A odb_String specifying the path to an existing output database (`.odb`) file.

*readOnly*

A Boolean specifying whether the file will permit only read access or both read and write access. The initial value is False, indicating that both read and write access will be permitted.

**Return value**

An Odb object.

**Exceptions**

If the output database was generated by a previous release of Abaqus and needs upgrading:

```
OdbError: The database is from a previous release of Abaqus. Run `abaqus upgrade `
```

```
`-job <*newFilename*> -odb <*oldFileName*>` to upgrade it.
```

If the output database was generated by a newer release of Abaqus, and the installation of Abaqus needs upgrading:

```
OdbError: Abaqus installation must be upgraded before this output database can be opened.
```

If the file is not a valid database:

```
AbaqusException: Cannot open file <*filename*>.
```

### 61.32.6 upgradeOdb(...)

This method upgrades an existing Odb object to the current release and writes the upgraded version of the Odb object to a file. In addition, Abaqus/CAE writes information about the status of the upgrade to a log (`*.log`) file.

**Prototype**

```
void upgradeOdb(const odb_String& existingOdbPath,
const odb_String& upgradedOdbPath);
```

**Required arguments**

*existingOdbPath*

An odb_String specifying the path to the file containing the output database to be upgraded.

*upgradedOdbPath*

An odb_String specifying the path to the file that will contain the upgraded output database.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

If the output database upgrade fails:

```
OdbError: cannot convert database
```

### 61.32.7 getActiveOdb(...)

This method is intended to be used inside an Abaqus/Standard or Abaqus/Explicit user subroutine written in C++. It fetches the  object that is in use by the analysis product and enables a user to modify it inside the user subroutine. This method will throw an exception if more than one output database is currently open.

**Prototype**

```
odb_Odb& getActiveOdb();
```

**Arguments**

None.

**Return value**

An  object.

**Exceptions**

If more than one output database file is open:

```
OdbError: The getActiveOdb method can only be called if a single odb file is open.
```

If no output database files are open:

```
OdbError: No odb files are open.
```

None.

### 61.32.8 odb_IsA(...)

This method takes a type and a base object and returns a boolean indicating whether the subtype of the supplied base object matches the type argument. This method is useful when fetching base Section, Profile, or Amplitude objects from their containers. If, for example, the user wants to determine if the base odb_Section object returned by the odb_SectionContainer is actually of type odb_BeamSection, he would call this method with the odb_BeamSection as the type and the odb_Section object as the base object.

**Prototype**

```
bool odb_IsA(TYPE, const BASETYPE& obj);
```

**Required arguments**

*TYPE*

The potential type of the base class object.

*obj*

The base object being tested for the TYPE.

**Optional arguments**

None.

**Return value**

A Boolean.

**Exceptions**

None.

### 61.32.9 odb_dynamicCast(...)

This method casts a supplied Section, Profile, or Amplitude to the specified subtype. This method is useful for retrieving the base objects out of the appropriate containers and casting them to the subtype to access the data members for that particular subtype. This method will throw an odb_BaseException if the cast is not possible.

**Prototype**

```
const TYPE& returnObj = odb_dynamicCast(TYPE, const BASETYPE& obj);
```

**Required arguments**

*TYPE*

The potential type of the base class object.

*obj*

The base object being case to TYPE.

**Optional arguments**

None.

**Return value**

An object of type TYPE.

**Exceptions**

If the cast is not possible:

```
Bad cast: From BASETYPE To TYPE.
```




