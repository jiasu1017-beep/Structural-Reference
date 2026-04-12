# AFXSymConstKeyword







This class is designed for the command keywords that have symbolic constant values. 
![](../graphics/gui-afxsymconstkeyword.png)

### AFXSymConstKeyword(command, name, isRequired=False, defaultValue=0)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| command | AFXCommand |  | Host command. |
| name | String |  | Keyword name. |
| isRequired | Bool | False | True if the keyword is a required argument of the command. |
| defaultValue | Int | 0 | Default value. |

### getTypeName()

Returns the name of the keyword type.

Reimplemented from AFXIntKeyword.

### getValueAsString()

Returns the text string that represents the keyword's current value.

Reimplemented from AFXIntKeyword.

### setDefaultValue(defaultValue)

Sets the keyword's default value.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| defaultValue | Int |  | Default value. |

### setDefaultValueByString(defaultValueString)

Sets the keyword's default value (returns True if the given text string is valid).
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| defaultValueString | String |  | Default value in text string form. |

### setDefaultValueByString(defaultValueString)

Sets the keyword's default value (returns True if the given text string is valid).
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| defaultValueString | String |  | Default value in text string form. |

### setValue(newValue)

Sets the keyword's current value.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| newValue | Int |  | New value. |

### setValueByString(newValueString)

Sets the keyword's current value (returns True if the given text string is valid).
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| newValueString | String |  | New value in text string form. |

### setValueByString(newValueString)

Sets the keyword's current value (returns True if the given text string is valid).
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| newValueString | String |  | New value in text string form. |

### setValueToDefault(ignoreUnspecified=False)

Sets the keyword value to its default.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| ignoreUnspecified | Bool | False | Ignore setting the value if the default is unspecified. |




