# AFXPickStep





此类用于在 GUI 过程中提供拾取步骤。
![](../graphics/gui-afxpickstep.png)

### AFXPickStep(owner, keyword, prompt, entitiesToPick, numberToPick=ONE, highlightLevel=1, sequenceStyle=ARRAY)

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| owner | AFXProcedure |  | 创建步骤的过程。 |
| keyword | AFXObjectKeyword |  | 包含拾取变量的对象关键字。作为 AFXGuiCommand 的一部分。 |
| prompt | String |  | 在提示区域显示的步骤提示。 |
| entitiesToPick | Int |  | 要拾取的实体类型。 |
| numberToPick | pickAmountEnum | ONE | 要拾取的实体数量。 |
| highlightLevel | Int | 1 | 高亮级别。 |
| sequenceStyle | sequenceStyleEnum | ARRAY | 命令中拾取变量的序列样式。 |

### addElementSetSelection(name)

将元素集添加到步骤的选择中。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| name | String |  | 集的名称。 |

### addGeometrySetSelection(name)

将几何集添加到步骤的选择中。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| name | String |  | 集的名称。 |

### addNodeSetSelection(name)

将节点集添加到步骤的选择中。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| name | String |  | 集的名称。 |

### addPointKeyIn(keyword)

在提示行上创建一个文本字段作为指定点的替代方法。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| keyword | AFXTupleKeyword |  | 关键字。 |

### addSurfaceSelection(name)

将曲面添加到步骤的选择中。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| name | String |  | 曲面的名称。 |

### allowRepeatedSelections(value=True)

允许拾取先前的选择（来自过程先前的拾取步骤）。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| value | Bool | True | 如果为 True，则允许步骤之间重复选择。 |

### onCancel()

当步骤被取消时调用。

从 AFXStep 重实现。

在 AFXOrderedPickStep 中重实现。

### onExecute()

调用以执行 getFirstStep 和 getNextStep 返回的步骤。

从 AFXStep 重实现。

在 AFXOrderedPickStep 中重实现。

### onResume()

当步骤恢复时调用。

从 AFXStep 重实现。

### onSuspend()

当步骤被暂停时调用。

从 AFXStep 重实现。

### reset()

允许步骤在循环时重置其任何数据（如果需要）。

从 AFXStep 重实现。

在 AFXOrderedPickStep 中重实现。

### setEdgeRefinements(refinement)

设置拾取边时使用的细化。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| refinement | Int |  | 细化标志。 |

### setElementEdgeRefinements(refinement)

设置拾取元素边时使用的细化。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| refinement | Int |  | 细化标志。 |

### setElementFaceRefinements(refinement)

设置拾取元素面时使用的细化。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| refinement | Int |  | 细化标志。 |

### setElementRefinements(refinement)

设置拾取元素时使用的细化。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| refinement | Int |  | 细化标志。 |

### setFaceRefinements(refinement)

设置拾取面时使用的细化。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| refinement | Int |  | 细化标志。 |

### setInstanceRefinements(refinement)

设置拾取实例时使用的细化。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| refinement | Int |  | 细化标志。 |

### setNodeRefinements(refinement)

设置拾取节点时使用的细化。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| refinement | Int |  | 细化标志。 |

### setSketchRefinements(refinement)

设置拾取草图时使用的细化。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| refinement | Int |  | 细化标志。 |

### setXyRefinements(refinement)

设置拾取 xy 对象时使用的细化。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| refinement | Int |  | 细化标志。 |

### 类标志

### **拾取实体数量的标志。**

| **ONE** | 只允许拾取一个实体。 |
| --- | --- |
| **MANY** | 允许拾取一个或多个实体。 |

### **细化可拾取实体的标志。**

| **STRAIGHT** | 只允许拾取直线实体。 |
| --- | --- |
| **WIRE** | 只允许拾取线框实体。 |
| **PLANAR** | 只允许拾取平面实体。 |
| **CONICAL** | 只允许拾取圆锥实体。 |
| **SHELL** | 只允许拾取壳实体。 |
| **ORPHAN_MESH** | 只允许拾取孤立网格实体。 |
| **SOLID** | 只允许拾取实体。 |
| **GEOMETRY** | 只允许拾取几何实体。 |
| **POINT** | 只允许拾取点实体。 |
| **BACKGROUND** | 草图时只允许拾取背景实体。 |
| **FOREGROUND** | 只允许拾取草图实体。 |
| **VERTICAL** | 只允许拾取垂直几何草图实体。 |
| **HORIZONTAL** | 只允许拾取水平几何草图实体。 |
| **CONSTRUCTION** | 只允许拾取构造草图实体。 |
| **NO_CONSTRUCTION** | 只允许拾取非构造几何草图实体。 |
| **SPOT** | 只允许拾取点草图实体。 |
| **CIRCULAR** | 只允许拾取圆形草图实体。 |
| **INTERIOR** | 只允许拾取内部实体。 |
| **EXTERIOR** | 只允许拾取外部实体。 |

### **可拾取实体的标志。**

| **VERTICES** | 允许拾取顶点。 |
| --- | --- |
| **EDGES** | 允许拾取边。 |
| **FACES** | 允许拾取面。 |
| **CELLS** | 允许拾取单元。 |
| **STRINGERS** | 允许拾取纵肋。 |
| **SKINS** | 允许拾取蒙皮。 |
| **ELEMENT_EDGES** | 允许拾取元素边。 |
| **ELEMENT_FACES** | 允许拾取元素面。 |
| **NODES** | 允许拾取节点。 |
| **ELEMENTS** | 允许拾取单元。 |
| **INSTANCES** | 允许拾取模型数据库中的零件实例。 |
| **MAX_DIMENSION** | 只允许拾取最高维度（1D、2D、3D）的对象。 |
| **REFERENCE_POINTS** | 允许拾取参考点。 |
| **INTERESTING_POINTS** | 允许拾取有趣点。 |
| **DATUM_POINTS** | 允许拾取基准点。 |
| **DATUM_AXES** | 允许拾取基准轴。 |
| **DATUM_PLANES** | 允许拾取基准平面。 |
| **DATUM_CSYS** | 允许拾取基准坐标系。 |
| **REMOVABLE_EDGES** | 允许从面选择中移除边。 |
| **FEATURES** | 允许拾取特征。 |
| **SKETCH_VERTICES** | 允许拾取草图顶点。 |
| **SKETCH_GEOMETRIES** | 允许拾取草图几何。 |
| **SKETCH_DIMENSIONS** | 允许拾取草图尺寸。 |
| **SKETCH_CONSTRAINTS** | 允许拾取草图约束。 |
| **SKETCH_COORDINATES** | 允许拾取草图坐标，必须添加键盘输入。 |
| **SKIN_ELEMENTS** | 允许拾取蒙皮上的单元。 |
| **STRINGER_ELEMENTS** | 允许拾取纵肋上的单元。 |
| **POINTS** | 允许拾取所有类型的点。 |
| **LINES** | 允许拾取所有类型的线。 |
| **PLANES** | 允许拾取所有类型的平面。 |

### **拾取项目的命令序列样式标志。**

| **TUPLE** | 指定为逗号分隔的单个项目元组。 |
| --- | --- |
| **ARRAY** | 指定为加号分隔的序列项目。 |


