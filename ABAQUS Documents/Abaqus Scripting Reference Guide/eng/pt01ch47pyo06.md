# 47.6 JournalOptions object







A JournalOptions               object specifies how to record selection of geometry in the journal and replay files. *journalOptions*               can also be used to set the numeric formatting options for field report output, geometry commands output, and a default format for other numeric output. The JournalOptions               object has no constructor. Abaqus creates the *journalOptions*               member when a session is started.

**Access**

```
session.journalOptions
```

### 47.6.1 setValues(...)

This method modifies the JournalOptions                     object.

**Required arguments**

None.

**Optional arguments**

*replayGeometry*

A SymbolicConstant specifying the format of the geometry in the replay file. Possible values are COORDINATE, INDEX, and COMPRESSEDINDEX. The default value is COMPRESSEDINDEX.

*recoverGeometry*

A SymbolicConstant specifying the format of the geometry in the recovery file. Possible values are COORDINATE, INDEX, and COMPRESSEDINDEX. The default value is COMPRESSEDINDEX.

*defaultFormat*

A [NumberFormat](pt01ch47pyo09.md) object specifying the default format for numeric output. The default values are the same as the default values for the [NumberFormat](pt01ch47pyo09.md)                     object.

*fieldReportFormat*

A [NumberFormat](pt01ch47pyo09.md) object specifying the default format for numbers in a field report output. The default values are the same as the default values for the [NumberFormat](pt01ch47pyo09.md)                     object.

*geometryFormat*

A [NumberFormat](pt01ch47pyo09.md) object specifying the default format for numbers in geometry commands output. The default values are the same as the default values for the [NumberFormat](pt01ch47pyo09.md)                     object.

**Return value**

None

**Exceptions**

None.

### 47.6.2 Members

The JournalOptions object has members with the same names and descriptions as the arguments to the [setValues](pt01ch47pyo06.md#ker-journaloptions-setvalues-pyc) method.




