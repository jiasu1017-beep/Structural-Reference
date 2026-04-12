# 1.2 CaeGuiPrefs object







The CaeGuiPrefs object contains the details of the graphical preferences in a `guiPreferences` section of the `abaqus_v6.14.gpr` file.

**Access**

```
import caePrefsAccess
caePrefsAccess.openGuiPreferences(...)
```

### 1.2.1 save(...)

This method saves the `guiPreferences` section specified in the current *fileName*.

**Required arguments**

None.

**Optional argument**

*backupFile*

A Boolean specifying whether Abaqus should save a numbered backup copy of the preferences file, *fileName*. Default is True.

**Return value**

None

**Exceptions**

None.

### 1.2.2 saveAs(...)

This method saves the `guiPreferences` settings to the specified location.

**Required argument**

*fileName*

A String specifying the path to the preferences file.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 1.2.3 Members

The CaeGuiPrefs object has the following member:

*fileName*

A String specifying the path to the preferences file.




