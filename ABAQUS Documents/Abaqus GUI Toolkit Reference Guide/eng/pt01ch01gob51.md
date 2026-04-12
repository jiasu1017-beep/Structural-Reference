# AFXStringKeyword







This class is designed for the command keywords that have text string values. 
![](../graphics/gui-afxstringkeyword.png)

### AFXStringKeyword(command, name, isRequired=False, defaultValue='')

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| command | AFXCommand |  | Host command. |
| name | String |  | Keyword name. |
| isRequired | Bool | False | True if the keyword is a required argument of the command. |
| defaultValue | String | '' | Default value. |

### getTypeName()

Returns the name of the keyword type.

Implements AFXKeyword.

### getValue()

Returns the keyword's current value.

### getValueAsString()

Returns the text string that represents the keyword's current value.

Implements AFXKeyword.

### isValueChanged()

Returns True if the keyword value differs from its previous value.

Implements AFXKeyword.

### setDefaultValue(defaultValue)

Sets the keyword's default value.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| defaultValue | String |  | Default value. |

### setValue(newValue)

Sets the keyword's current value.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| newValue | String |  | New value. |

### setValueToDefault(ignoreUnspecified=False)

Sets the keyword value to its default.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| ignoreUnspecified | Bool | False | Ignore setting the value if the default is unspecified. |

### setValueToPrevious()

Sets the keyword value to its previous value.

Implements AFXKeyword.

### syncPreviousValue()

Sets the keyword's previous value to its current value.

Implements AFXKeyword.




