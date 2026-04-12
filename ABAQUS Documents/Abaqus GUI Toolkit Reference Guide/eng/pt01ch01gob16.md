# AFXFloatKeyword







This class is designed for the command keywords that have floating-point values. 
![](../graphics/gui-afxfloatkeyword.png)

### AFXFloatKeyword(command, name, isRequired=False, defaultValue=FLOAT_DEFAULT, precision=6)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| command | AFXCommand |  | Host command. |
| name | String |  | Keyword name. |
| isRequired | Bool | False | True if the keyword is a required argument of the command. |
| defaultValue | Float | FLOAT_DEFAULT | Default value. |
| precision | Int | 6 | Precision for converting the keyword's floating-point value to a text string. |

### getPrecision()

Returns the precision that is used for converting the keyword's floating-point value to a text string.

### getTypeName()

Returns the name of the keyword type.

Implements AFXKeyword.

### getValue()

Returns the keyword's current value, or zero if the content expression is invalid.

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

### setDefaultValue(defaultValue)

Sets the keyword's default value.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| defaultValue | Float |  | Default value. |

### setPrecision(precision)

Sets the precision that is used for converting the keyword's floating-point value to a text string.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| precision | Int |  |  |

### setValue(newValue)

Sets the keyword's current value.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| newValue | String |  | New value. |

### setValue(newValue)

Sets the keyword's current value.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| newValue | Float |  | New value. |

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




