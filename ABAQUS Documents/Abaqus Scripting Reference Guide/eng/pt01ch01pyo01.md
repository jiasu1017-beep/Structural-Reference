# 1.1 caePrefsAccess module







The Python module `caePrefsAccess` contains functions that enable you to edit the Abaqus/CAE preferences file, `abaqus_v6.14.gpr`.

**Access**

```
import caePrefsAccess
```

### 1.1.1 getGuiPrefsFileName(...)

This function enables you to retrieve the location of your `abaqus_v6.14.gpr` file.

**Path**

```
caePrefsAccess.getGuiPrefsFileName
```

**Return value**

A String with the default file name for the GUI preferences file.

### 1.1.2 getDisplayNamesInGuiPreferences(...)

The `abaqus_v6.14.gpr` file stores a separate `guiPreferences` record for each display that you use. This function returns a list of every displayName recorded in the preferences file. 

**Path**

```
caePrefsAccess.getDisplayNamesInGuiPreferences
```

**Required argument**

*fileName*

A String that specifies the path to the preferences file.

**Optional arguments**

None.

**Return value**

A list of Strings of displayNames.

**Exceptions**

None.

### 1.1.3 printValuesList(...)

This function enables you to print all of the options and their values for a set of `guiPreferences` or `sessionOptions` settings derived from the `abaqus_v6.14.gpr` file.

**Path**

```
caePrefsAccess.printValuesList
```

**Required argument**

*object*

The `guiPreferences` object or `sessionOptions` object for which you want to print options and their values.

**Optional arguments**

*maxRecursionDepth*

An Int, or SymbolicConstant UNLIMITED, that specifies the depth of recursion when accessing the attributes of *object*.

*asString*

A Boolean specifying how the string representation of each option is printed. If *asString* is True, `printValuesList` prints the `str` of each option; otherwise `printValuesList` prints the `repr` of the options.  The default value is False.

**Return value**

A String displaying the path, name, and value for all of the options in the object that you select.

**Exceptions**

None.

### 1.1.4 openGuiPreferences(...)

This function enables you to examine and change many default behaviors in the Abaqus/CAE graphical user interface. Abaqus stores preferences for each display you use in a separate `guiPreferences` section of the `abaqus_v6.14.gpr` file.

**Path**

```
caePrefsAccess.openGuiPreferences
```

**Required argument**

*displayName*

A String that specifies the display for which you want to investigate GUI preferences from the `abaqus_v6.14.gpr` file. You can retrieve the available display names in the file by using the `getDisplayNamesInGuiPreferences` method.

**Optional argument**

*fileName*

A String specifying the path to the preferences file. The `openGuiPreferences` method uses this argument if you are working with a preferences file that is not at the default location. 

        If this argument is omitted, the `abaqus_v6.14.gpr` file in your home directory is opened. 

**Return value**

A CaeGuiPrefs object.

**Exceptions**

None.

### 1.1.5 openSessionOptions(...)

This function enables you to examine and change the default behavior for many session options Abaqus/CAE; that is, the settings that you can save in Abaqus/CAE from the ****File**![](../graphics/images/arrow.gif)**Save Display Options**** menu option. Abaqus stores default session options in the `sessionOptions` section of the `abaqus_v6.14.gpr` file.

**Path**

```
caePrefsAccess.openSessionOptions
```

**Required arguments**

None.

**Optional arguments**

*fileName*

A String specifying the path to the preferences file. The `openSessionOptions` method uses this argument if you are working with a preferences file that is not at the default location. 

        If this argument is omitted, the `abaqus_v6.14.gpr` file in your home directory is opened. 

*directory*

A SymbolicConstant specifying the location of the preferences file. Possible values are:
- CURRENT to open the preferences file in the current directory (`caePrefsAccess`.CURRENT)
- HOME to open the preferences file in your home directory (`caePrefsAccess`.HOME)

The default value is HOME. Either *fileName* or *directory* must be supplied. The *fileName* or *directory* arguments are mutually exclusive.

**Return value**

A CaeKerPrefs object.

**Exceptions**

None.



