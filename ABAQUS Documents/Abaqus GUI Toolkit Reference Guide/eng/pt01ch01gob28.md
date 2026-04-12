# AFXKeyword







This class is the abstract base class for all command keywords. 
![](../graphics/gui-afxkeyword.png)

### AFXKeyword(command, name, isRequired=False)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| command | AFXCommand |  | Host command, or NULL to create a keyword not associated with a command. |
| name | String |  | Keyword name. |
| isRequired | Bool | False | True if the keyword is a required argument of the command. |

### activate()

Activates the keyword; active keywords will be processed during command generation.

### deactivate()

Deactivates the keyword; inactive keywords will not be processed during command generation.

### getCommandSnippet()

Returns the command snippet of the keyword based on its current value.

### getName()

Returns the keyword name.

### getSetupCommands()

Returns the keyword's variable initilization commands (part of the generated command string).

### getTypeName()

Returns the keyword type name.

Implemented in AFXBoolKeyword, AFXComSymConstKeyword, AFXComTableKeyword, AFXFloatKeyword, AFXIntKeyword, AFXObjectKeyword, AFXStringKeyword, AFXSymConstKeyword, AFXTogglableKeyword, AFXTupleKeyword, and AFXTableKeyword.

### getValueAsString()

Returns the text string that represents the current keyword value.

Implemented in AFXBoolKeyword, AFXComSymConstKeyword, AFXComTableKeyword, AFXFloatKeyword, AFXIntKeyword, AFXObjectKeyword, AFXStringKeyword, AFXSymConstKeyword, AFXTogglableKeyword, and AFXTupleKeyword.

### isActive()

Returns True if the keyword is active.

### isRequired()

Returns True if the keyword is a required argument of the host command; or returns False if the keyword is optional.

### isValueChanged()

Returns True if the keyword value differs from its previous value.

Implemented in AFXBoolKeyword, AFXComSymConstKeyword, AFXComTableKeyword, AFXFloatKeyword, AFXIntKeyword, AFXObjectKeyword, AFXStringKeyword, AFXTogglableKeyword, and AFXTupleKeyword.

### setRequired(val)

Sets this object as a required keyword of the host command.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| val | Bool |  |  |

### setSetupCommands(cmds)

Sets variable initialization commands needed by the keyword.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| cmds | String |  |  |

### setValueToDefault(ignoreUnspecified=False)

Sets the keyword value to its default.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| ignoreUnspecified | Bool | False | Ignore setting the value if the default is unspecified. |

### setValueToPrevious()

Sets the keyword value to its previous value.

Implemented in AFXBoolKeyword, AFXComSymConstKeyword, AFXComTableKeyword, AFXFloatKeyword, AFXIntKeyword, AFXObjectKeyword, AFXStringKeyword, AFXTogglableKeyword, and AFXTupleKeyword.

### syncPreviousValue()

Sets the keyword's previous value to its current value.

Implemented in AFXBoolKeyword, AFXComSymConstKeyword, AFXComTableKeyword, AFXFloatKeyword, AFXIntKeyword, AFXObjectKeyword, AFXStringKeyword, AFXTogglableKeyword, and AFXTupleKeyword.

### Class flags

### **Message ID's.**

| **ID_ACTIVATE** | Used to activate the keyword. |
| --- | --- |
| **ID_DEACTIVATE** | Used to deactivate the keyword. |




