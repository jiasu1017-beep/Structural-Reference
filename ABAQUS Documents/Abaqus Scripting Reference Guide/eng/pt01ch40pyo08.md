# 40.8 OdbData object







The OdbData object stores non persistent values and attributes associated with an open odb for the given session. The OdbData object has no constructor. Abaqus creates the *odbData* repository when you import the Visualization module.  Abaqus creates a OdbData object when an odb is opened.

**Access**

```
import visualization
session.odbData[*name*]
```

### 40.8.1 setValues(...)

This method modifies the OdbData object.

**Required arguments**

None.

**Optional arguments**

*activeFrames*

A sequence specifying the active frames, or the SymbolicConstant ALL. Each item in the sequence is a tuple defining the stepName followed by a sequence of expressions specifying frame numbers. The expression can be any of the following:
- An Int specifying a single frame number; for example, `1`.
- A String specifying a single frame number ; for example, `'7'`.
- A String specifying a sequence of frame numbers; for example, `'3:5'` and `'3:15:3'`.

 For these expressions a negative number will indicate reverse numbering: -1 is the last frame of the step, -2 is the one before the last frame. Frame numbering starts at 0.

*stepPeriods*

A sequence of (String, Float) sequences specifying the stepName and the stepPeriod. Alternatively, this member may take the value ODB_VALUES.

**Return value**

None

**Exceptions**

None.

### 40.8.2 Members

The OdbData object can have the following members:

*activeFrames*

A tuple specifying the active frames, or the SymbolicConstant ALL. Each item in the sequence is a tuple defining the stepName followed by a sequence of expressions specifying frame numbers. The expression can be any of the following:
- An Int specifying a single frame number; for example, `1`.
- A String specifying a single frame number ; for example, `'7'`.
- A String specifying a sequence of frame numbers; for example, `'3:5'` and `'3:15:3'`.

 For these expressions a negative number will indicate reverse numbering: -1 is the last frame of the step, -2 is the one before the last frame. Frame numbering starts at 0.

*stepPeriods*

A tuple of (String, Float) tuples specifying the stepName and the stepPeriod. Alternatively, this member may take the value ODB_VALUES.

*historyVariables*

A repository of [HistoryVariable](pt01ch40pyo07.md) objects specifying the history request label. The repository is read-only.

*steps*

A repository of [OdbDataStep](pt01ch40pyo16.md) objects specifying the list of steps. The repository is read-only.

*instances*

A repository of [OdbDataInstance](pt01ch40pyo12.md) objects specifying the list of instances. The repository is read-only.

*materials*

A repository of [OdbDataMaterial](pt01ch40pyo13.md) objects specifying the list of materials. The repository is read-only.

*sections*

A repository of [OdbDataSection](pt01ch40pyo15.md) objects specifying the list of sections. The repository is read-only.

*elementSets*

A repository of [OdbDataElementSet](pt01ch40pyo10.md) objects specifying the list of element sets. The repository is read-only.

*nodeSets*

A repository of [OdbDataNodeSet](pt01ch40pyo14.md) objects specifying the list of node sets. The repository is read-only.

*surfaceSets*

A repository of [OdbDataSurfaceSet](pt01ch40pyo17.md) objects specifying the list of surface sets. The repository is read-only.

*datumCsyses*

A repository of [OdbDataDatumCsys](pt01ch40pyo09.md) objects specifying the list of coordinate systems defined in the model. The repository is read-only.




