# AFXSequenceString





此类支持解析和修改包含用某个分隔符分隔的元素序列的字符串。
![](../graphics/gui-afxsequencestring.png)

### AFXSequenceString(value='', sep=',')

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| value | String | '' | 带初始序列值的字符串。 |
| sep | String | ',' | 序列元素的分隔符。 |

### AFXSequenceString()

未定义的复制构造函数（此类不具有复制语义）。

### forceNumElements(num, fill)

强制内容字符串包含具有给定元素数的元组。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| num | Int |  | 新的元素数量。 |
| fill | String |  | 插入空格的字符串。 |

### getContentString()

返回包含序列元素值的字符串。

在 AFX2DArrayConstString 中重新实现。

### getElementSeparator()

返回元素分隔符字符。

### getLength(index)

返回序列元素的长度（以字符为单位）。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |

### getNumElements()

返回此序列中的元素数量。

### getPosition(index)

返回序列元素起始字符在内容字符串中的位置。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |

### getValue(index)

返回序列元素的值。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |

### insert(index, numElements, val)

插入元素的多个副本。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  | 开始插入的元素索引。 |
| numElements | Int |  | 要插入的元素数量。 |
| val | String |  | 新元素的值。 |

### isValidSequence()

如果此对象包含有效序列，则返回 True。

### remove(index, numElements)

从给定索引开始移除元素。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  | 开始移除的元素索引。 |
| numElements | Int |  | 要移除的元素数量。 |

### setContentString(seqstr)

重置序列元素的所有值。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| seqstr | String |  | 带新值的序列字符串。 |

### setElementSeparator(sep)

设置元素分隔符字符。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| sep | String |  | 分隔符字符。 |

### setLength(index, length)

设置序列元素的长度。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |
| length | Int |  | 新长度（以字符为单位）。 |

### setPosition(index, position)

设置序列元素的位置。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |
| position | Int |  | 字符串中的新位置。 |

### setValue(index, value, replaceAll=False)

设置序列元素的值。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |
| value | String |  | 新值。 |
| replaceAll | Bool | False | 如果为 False（默认），则保留前导和尾随空格，否则替换分隔符之间的所有空格。 |

### trimWhiteSpace(index)

调整元素的位置和长度以修剪前导和尾随空格。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |



