# FXDataTarget





Data Target 允许将评估器 widget（如滑块或文本字段）直接连接到程序中的变量。每当评估器控件更改时，通过数据目标连接的变量会自动更新；反之，每当程序更改变量时，所有连接的评估器 widget 都会更新以在显示上反映这个新值。数据目标还允许将单选按钮、菜单命令等连接到变量。在这种情况下，连接变量的新值是通过从消息 ID 中减去 ID_OPTION 来计算的。
![](../graphics/gui-fxdatatarget.png)

### FXDataTarget(tgt=None, sel=0)

不关联任何对象。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| tgt | FXObject | None | |
| sel | Int | 0 | |

### FXDataTarget(value, tgt=None, sel=0)

与字符变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | String |  | |
| tgt | FXObject | None | |
| sel | Int | 0 | |

### FXDataTarget(value, tgt=None, sel=0)

与无符号字符变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Int |  | |
| tgt | FXObject | None | |
| sel | Int | 0 | |

### FXDataTarget(value, tgt=None, sel=0)

与有符号短变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Int |  | |
| tgt | FXObject | None | |
| sel | Int | 0 | |

### FXDataTarget(value, tgt=None, sel=0)

与无符号短变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Int |  | |
| tgt | FXObject | None | |
| sel | Int | 0 | |

### FXDataTarget(value, tgt=None, sel=0)

与 int 变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Int |  | |
| tgt | FXObject | None | |
| sel | Int | 0 | |

### FXDataTarget(value, tgt=None, sel=0)

与无符号 int 变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Int |  | |
| tgt | FXObject | None | |
| sel | Int | 0 | |

### FXDataTarget(value, tgt=None, sel=0)

与 float 变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Float |  | |
| tgt | FXObject | None | |
| sel | Int | 0 | |

### FXDataTarget(value, tgt=None, sel=0)

与 double 变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Float |  | |
| tgt | FXObject | None | |
| sel | Int | 0 | |

### FXDataTarget(value, tgt=None, sel=0)

与字符串变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | String |  | |
| tgt | FXObject | None | |
| sel | Int | 0 | |

### connect(value)

与字符串变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | String |  | |

### connect(value)

与 double 变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Float |  | |

### connect(value)

与 float 变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Float |  | |

### connect(value)

与无符号 int 变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Int |  | |

### connect(value)

与 int 变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Int |  | |

### connect(value)

与无符号短变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Int |  | |

### connect(value)

与有符号短变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Int |  | |

### connect(value)

与无符号字符变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | Int |  | |

### connect(value)

与字符变量关联。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| value | String |  | |

### connect()

不关联任何对象。

### getData()

返回指向其所连接数据的指针。

### getSelector()

获取此数据目标的消息标识符。

### getTarget()

获取此数据目标的消息目标对象（如果有）。

### getType()

返回其连接的数据类型。

### setSelector(sel)

设置此数据目标的消息标识符。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| sel | Int |  | |

### setTarget(t)

设置此数据目标的消息目标对象。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| t | FXObject |  | |

### 类标志

### ** **

| **ID_VALUE** | 将导致 FXDataTarget 向发送者请求值。 |
| --- | --- |
| **ID_OPTION** | ID_OPTION+i 会将值设置为 i，其中 -10000<=i<=10000。 |





