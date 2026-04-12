# 34.26 ScratchOdb object







A scratch output database is associated with an open output database and is used to store session-related, non-persistent objects, such as Step, Frame and [FieldOutput](pt01ch34pyo06.md) objects. Abaqus creates a scratch output database when needed for these non-persistent objects during an Abaqus/CAE session. Abaqus deletes the scratch output database when the associated output database is closed.

**Access**

```
import odbAccess
session.scratchOdbs[*name*]
```

### 34.26.1 ScratchOdb(...)

This method creates a new ScratchOdb object.

**Path**

```
session.ScratchOdb
```

**Required argument**

*odb*

An [Odb](pt01ch34pyo01.md) object specifying the output database with which to associate.

**Optional arguments**

None.

**Return value**

A ScratchOdb object.

**Exceptions**

None.

### 34.26.2 Members

The ScratchOdb object has no members.




