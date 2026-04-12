# AFXComTableKeyword







This class manages values which are sent as tables in a command.
![](../graphics/gui-afxcomtablekeyword.png)

### AFXComTableKeyword(command, name, isRequired=False, minLength=0, maxLength=-1, opts=0)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| command | AFXCommand |  | Host command. |
| name | String |  | Keyword name. |
| isRequired | Bool | False | True if this keyword is a required argument. |
| minLength | Int | 0 | Minimum (and default) row length. |
| maxLength | Int | -1 | Maximum row length (-1 => unlimited). |
| opts | Int | 0 | Options. |

### equal(index, a, b)

Returns True if the two table element values compare equal (index not used).
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Element index (not used). |
| a | String |  | First value. |
| b | String |  | Second value. |

### getColumnStyle(index)

Returns the style of the column elements. Will never return AFXTABLE_STYLE_DEFAULT!
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Column index. |

### getColumnType(index)

Returns the type of the column elements. Will never return AFXTABLE_TYPE_DEFAULT!
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Column index. |

### getDefaultStyle()

Returns the default style for the table elements.

### getDefaultType()

Returns the default type for the table elements.

### getDefaultValues()

Returns the default values for this table.

### getFormattedValue(row, column)

Returns the formatted value of the table element, suitable for placing in a command. If the element has AFXTABLE_EVALUATE style, and its contents are invalid, an exception will be thrown.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| row | Int |  | Row index. |
| column | Int |  | Column index. |

### getMaxNumColumns()

Returns the maximum number of columns, or -1 for unbounded.

### getMinNumColumns()

Returns the minimum number of columns.

### getNumColumns(row)

Returns the number of columns in the row.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| row | Int |  | Row index. |

### getNumRows()

Returns the number of rows in the table.

### getRow(row)

Returns a string with the contents of a table row.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| row | Int |  | Row index. |

### getTypeName()

Returns the name of the table keyword type.

Implements AFXKeyword.

Reimplemented in AFXTableKeyword.

### getValue(row, column)

Returns the value of a table element.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| row | Int |  | Row index. |
| column | Int |  | Column index. |

### getValueAsDouble()

Returns the keyword's value as a float; returns False upon failure.

### getValueAsInt()

Returns the keyword's value as an integer; returns False upon failure.

### getValueAsString()

Returns the formatted string that represents the current keyword value in a command.

Implements AFXKeyword.

### getValueForBlank(column)

Returns the element value substituted for blank for the column.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| column | Int |  | Column index. |

### getValues()

Returns a string containing values of the tuple elements. as entered by the user.

### getValuesForBlanks()

Returns a string with values substituted for blanks for all table columns.

### insertColumns(index, numColumns)

Inserts columns starting at the given index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Starting index. |
| numColumns | Int |  | Number of columns to insert. |

### insertRows(index, numRows)

Inserts rows starting at the given index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Starting index. |
| numRows | Int |  | Number of rows to insert. |

### isValueChanged()

Returns True if the keyword value differs from its previous value.

Implements AFXKeyword.

### removeColumns(index, numColumns)

Removes columns starting at the given index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Starting index. |
| numColumns | Int |  | Number of columns to remove. |

### removeRows(index, numRows)

Removes rows starting at the given index.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Starting index. |
| numRows | Int |  | Number of rows to remove. |

### setColumnStyle(index, style)

Sets the style of the column elements.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Column index. |
| style | Int |  | New column style. |

### setColumnType(index, type)

Sets the type of the column elements.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| index | Int |  | Column index. |
| type | Int |  | New column type. |

### setDefaultStyle(style)

Sets the default style for the table elements.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| style | Int |  | New default style. |

### setDefaultType(type)

Sets the default type for table elements.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| type | Int |  | New default type. |

### setDefaultValues(values)

Sets the default values for this table.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| values | String |  | Sequence string with default values. |

### setMaxNumColumns(length)

Sets the maximum number of columns.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| length | Int |  | New maximum number of columns, or -1 for unbounded. |

### setMinNumColumns(length)

Sets the minimum number of columns.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| length | Int |  | New minimum length. |

### setNumColumnsRange(minLength, maxLength)

Sets the allowable range for the number of columns.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| minLength | Int |  | New minimum number of columns. |
| maxLength | Int |  | New maximum number of columns, or -1 for unbounded. |

### setRow(row, seq)

Sets the contents of a table row.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| row | Int |  | Row index. |
| seq | String |  | Sequence with elements. |

### setValue(row, column, value)

Sets the value of a table element.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| row | Int |  | Row index. |
| column | Int |  | Column index. |
| value | String |  | New value. |

### setValueForBlank(column, value)

Sets the element value substituted for blank for the column.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| column | Int |  | Column index. |
| value | String |  | New value. |

### setValues(values)

Sets all values for the table elements.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| values | String |  | Table string with new values. |

### setValuesForBlanks(values)

Sets the values substituted for blanks for all table columns.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| values | String |  | String containing comma-separated values. |

### setValueToDefault(ignoreUnspecified=False)

Sets the keyword value to its default.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| ignoreUnspecified | Bool | False | Should ignore if default is an unspecified value. |

### setValueToPrevious()

Sets the keyword value to its previous value.

Implements AFXKeyword.

### syncPreviousValue()

Sets the keyword's previous value to its current value.

Implements AFXKeyword.

### Class flags

### **Message ID's.**

| **ID_TABLE** | ID for AFXTable widgets. |
| --- | --- |
| **ID_VALUE** | ID for widgets exchanging array strings. |
| **ID_PRINTSNIPPET** | For debugging. |

### Global flags

### **Flags for table options.**

| **AFXTABLE_TYPE_ANY** | Any type is accepted. |
| --- | --- |
| **AFXTABLE_TYPE_DEFAULT** | Column type is the same as the table default type. |
| **AFXTABLE_TYPE_INT** | Column stores integer numbers. |
| **AFXTABLE_TYPE_FLOAT** | Column stores floating-point numbers. |
| **AFXTABLE_TYPE_STRING** | Column stores string values. |
| **AFXTABLE_TYPE_BOOL** | Column stores True or False. |
| **AFXTABLE_TYPE_MASK** | Mask for column types. |
| **AFXTABLE_ALLOW_EMPTY** | Allow empty values for the column elements. |
| **AFXTABLE_DEFAULT_IF_EMPTY** | Always substitute the default for empty values. |
| **AFXTABLE_EVALUATE** | Evaluate integer and float elements. |
| **AFXTABLE_STYLE_DEFAULT** | Use table default column style. |
| **AFXTABLE_STYLE_MASK** | Mask for column styles. |




