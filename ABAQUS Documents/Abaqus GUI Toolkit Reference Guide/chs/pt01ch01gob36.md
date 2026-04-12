# AFXModuleGui





此类是模块 GUI 的基类，提供模块 GUI 管理的接口。
![](../graphics/gui-afxmodulegui.png)

### AFXModuleGui(moduleName, displayTypes)

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| moduleName | String |  | 用于标识此模块的名称。 |
| displayTypes | Int |  | 此模块可能显示的主要对象类型。 |

### activate()

在切换过程中激活模块（允许特定于模块的激活要求）。

### deactivate()

在切换时停用模块（允许特定于模块的停用要求）。

### getModuleName()

返回构造时给出的模块名称。

### getToolsetKernelInitializationCommands()

返回为 kernel 中与模块 GUI 注册的工具集进行初始化的命令字符串。

### getTypesToDisplay()

返回此模块处于活动状态时可能显示的主要对象的类型（这目前假定为单一类型）。

### hide(location)

停用并隐藏模块在菜单栏、工具栏和工具箱中的 GUI 组件。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| location | Int |  | GUI 组件放置的位置。 |

### registerProcedureToolset(tool)

注册过程工具集（在派生模块构造期间调用）。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| tool | AFXProcedureToolsetGui |  | 正在注册的过程工具集的指针。 |

### registerToolset(tool, opts)

注册工具集（在派生模块构造期间调用）。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| tool | AFXToolsetGui |  | 正在注册的工具集的指针。 |
| opts | Int |  | 创建工具集 GUI 组件的选项。 |

### show(location)

激活并在菜单栏、工具栏和工具箱中显示模块的 GUI 组件。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| location | Int |  | GUI 组件放置的位置。 |

### unregisterToolset(name)

取消注册工具集。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| name | String |  | 要取消注册的工具集名称。 |

### 类标志

### **消息ID。**

| **MISSING ENUMERATOR** | MISSING ENUMERATOR DESCRIPTION |
| --- | --- |

### **对象显示的标志。**

| **PART** | 显示零件主要对象。 |
| --- | --- |
| **ASSEMBLY** | 显示装配主要对象。 |
| **ODB** | 显示 ODB 主要对象。 |
| **XY_PLOT** | 显示 XY 绘图主要对象。 |
| **SKETCH** | 显示草图主要对象。 |


