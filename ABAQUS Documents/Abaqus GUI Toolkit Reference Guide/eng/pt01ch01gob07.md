# AFXCommand







This class is the abstract base class for command classes that are processed by modes. 
![](../graphics/gui-afxcommand.png)

### AFXCommand(mode, method, objectName='', registerQuery=False)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| mode | AFXMode |  | Host mode. |
| method | String |  | Method. |
| objectName | String | '' | Object name. |
| registerQuery | Bool | False | True if a query should be registered when the command is used for the GUI. |

### activate()

Activates the command; active commands will be processed during command generation.

### deactivate()

Deactivates the command; inactive commands will not be processed during command generation.

### getCommandString()

Returns the command string based on the current values of the active keywords.

### getExpandedObjectName()

Returns the expanded object name that has all the "%s"'s replaced by the current names.

### getKeyword(name)

Returns the keyword with the given name (returns 0 if none is found).
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| name | String |  | Keyword name. |

### getKeyword(index)

Returns the keyword at the given index (returns 0 if the index is out-of-bounds).
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Keyword index (0-based). |

### getMethod()

Returns the command's method.

### getNumKeywords()

Returns the number of keywords.

### getObjectName()

Returns the object name (which is not expanded and may include "%s"'s).

### isActive()

Returns True if the command is active.

### isQueryNeeded()

Returns True if the command needs to register a query for kernel state.

### isRequired()

Returns True if this command is going to be sent even if none of its keywords has been modified, otherwise returns False.

### setKeywordValuesToDefaults(ignoreUnspecified=False)

Sets the values of all keywords to their defaults.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| ignoreUnspecified | Bool | False | Ignore setting the value if the default is unspecified. |

### setKeywordValuesToPrevious()

Sets the values of all keywords to their previous values.

### setMethod(method)

Sets the command's method.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| method | String |  | Method. |

### setObjectName(objectName)

Sets the object name.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| objectName | String |  | Object name. |

### setRequired(val)

Sets this command as required or optional; if True the command will always be sent, if False the command will be sent only if it has modified keywords or if it has no keywords.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| val | Bool |  |  |

### syncKeywordPreviousValues()

Synchronizes the current values and previous values of all keywords.

### verify()

Throws an exception if any of the keywords contain invalid data.




