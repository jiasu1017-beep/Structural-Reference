# *SUBSTRUCTURE GENERATE





### *SUBSTRUCTURE GENERATE子结构生成分析。

此选项用于指示该步应作为子结构生成步进行分析。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**此选项在以部件实例装配定义的模型中不受支持。

**Abaqus/CAE：**Step模块

##### **参考：**

- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)

### **必需参数：**

TYPE

将此参数设置为要分配给子结构库中此子结构的标识符。标识符必须是*Z*后跟不超过9999的数字。

子结构标识符在库中必须唯一。如果库中已存在具有此相同标识符的子结构，则除非指定了OVERWRITE参数，否则分析将终止并显示错误消息。

### **可选参数：**

ELSET

如果需要单元输出恢复，则在选择性恢复节点集中仅包含所有单元节点通常是不够的，因为单元可以具有Abaqus内部节点。

将此参数设置为包含要恢复结果的子结构区域中所有元素的元素集名称。

GRAVITY LOAD

设置GRAVITY LOAD=YES以计算子结构的重力载荷向量。默认值为GRAVITY LOAD=NO。

LIBRARY

将此参数设置为将写入子结构数据的子结构库名称。有关此类库名称的语法，请参见["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)。默认库名称为*jobname*。

MASS MATRIX

设置MASS MATRIX=YES以计算子结构的缩减质量矩阵。默认值为MASS MATRIX=NO。

NSET

将此参数设置为包含要恢复结果的子结构节点的节点集名称。此节点集必须包含可以在子结构使用分析中请求节点输出的所有节点。

如果省略NSET参数但使用了ELSET参数，则生成与指定元素集中所有单元节点对应的恢复矩阵。如果同时使用了NSET和ELSET参数，则生成节点集与元素集中所有元素的所有单元节点的并集的恢复矩阵。如果同时省略了NSET和ELSET参数，则生成所有消除节点的恢复矩阵（默认情况）。

OVERWRITE

包含此参数以覆盖库中具有相同TYPE标识符的现有子结构。默认是不覆盖。

PROPERTY EVALUATION

将此参数设置为在子结构生成期间评估粘弹性、弹簧和阻尼器频率相关属性的频率。如果省略此参数，Abaqus/Standard将在零频率评估与频率相关弹簧和阻尼器相关的刚度，并且不会考虑[*SUBSTRUCTURE GENERATE](ch18abk42.md)步中频域粘弹性的刚度贡献。

RECOVERY MATRIX

设置RECOVERY MATRIX=NO以指定在此子结构中不可用单元或节点信息输出。默认值为RECOVERY MATRIX=YES，表示对于大多数分析过程可以恢复已消除变量。

如果RECOVERY MATRIX=NO，则忽略NSET和ELSET参数。

STRUCTURAL DAMPING MATRIX

设置STRUCTURAL DAMPING MATRIX=YES以计算子结构的缩减结构阻尼矩阵。默认值为STRUCTURAL DAMPING MATRIX=NO。

VISCOUS DAMPING MATRIX

设置VISCOUS DAMPING MATRIX=YES以计算子结构的缩减粘性阻尼矩阵。默认值为VISCOUS DAMPING MATRIX=NO。

**此选项没有关联的数据行。**




