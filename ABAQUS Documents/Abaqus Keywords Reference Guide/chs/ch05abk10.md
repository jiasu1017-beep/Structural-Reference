# *ELEMENT OUTPUT









### *ELEMENT OUTPUT定义单元变量的输出数据库请求。

此选项用于将单元变量写入输出数据库。它必须与[*OUTPUT](ch15abk03.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**历史数据

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["输出到输出数据库，" Abaqus分析用户指南第4.1.3节](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **当[*ELEMENT OUTPUT](ch05abk10.md)选项与[*OUTPUT](ch15abk03.md)，HISTORY选项结合使用时，除非仅请求整个模型输出变量，否则需要以下互斥参数之一：**

ELSET

将此参数设置为正在为其发出输出请求的单元集名称。

TRACER SET

此参数仅适用于使用自适应性的Abaqus/Explicit分析。

将此参数设置为正在为其发出输出请求的追踪器集名称。

### **当[*ELEMENT OUTPUT](ch05abk10.md)选项与[*OUTPUT](ch15abk03.md)，FIELD选项结合使用时使用的可选参数：**

DIRECTIONS

此参数仅适用于Abaqus/Standard和Abaqus/Explicit分析。

设置 DIRECTIONS=YES（默认）以将单元材料方向写入输出数据库。设置 DIRECTIONS=NO 以指示不应将单元材料方向写入输出数据库。

ELSET

将此参数设置为正在为其发出输出请求的单元集名称。

如果省略此参数和EXTERIOR参数，将为模型中的所有单元写入输出。

EXTERIOR

此参数仅适用于Abaqus/Standard和Abaqus/Explicit分析。

包含此参数以将输出限制为仅外部三维单元。

如果省略此参数和ELSET参数，将为模型中的所有单元写入输出。

POSITION

如果值被写入单元质心（壳单元参考表面的质心，梁单元端节点之间的中点），则设置 POSITION=CENTROIDAL。在Abaqus/CFD中，单元输出始终使用 POSITION=CENTROIDAL。

如果值被写入实际计算变量的积分点，则设置 POSITION=INTEGRATION POINTS（默认）。

如果正在写入的值被外推到集合中每个单元的节点但不在节点处平均，则设置 POSITION=NODES。

### **可选参数：**

REBAR

此参数仅适用于膜、壳和表面单元中的钢筋。

此参数可用于仅获取指定单元集中钢筋的输出；不会给出基体材料的输出。它可以带值或不带值使用。如果不带值使用，则将为单元集中的所有钢筋给出输出。可以将其设置为[*REBAR LAYER](ch17abk12.md)选项上分配给钢筋的名称，以指定该特定钢筋在单元集中的输出。

如果在包含钢筋的模型中省略此参数，则输出请求控制仅基体材料的输出（截面力除外，其中钢筋中的力包含在力计算中）。

钢筋输出只能在膜、壳或表面单元的积分点和单元质心处获取。

VARIABLE

设置 VARIABLE=ALL 以指示所有适用于此过程和材料类型的单元变量都应写入输出数据库。

设置 VARIABLE=PRESELECT 以指示当前过程类型的默认单元输出变量应写入输出数据库。可以在数据行上请求其他输出变量。

如果省略此参数，则必须在数据行上指定要输出的单元变量。

### **请求单元输出的数据行：**

**第一行（可选，且仅在Abaqus/Standard分析中为壳、梁或分层实体单元写入积分点变量时，或在Abaqus/Explicit分析中为壳或梁单元写入积分点变量时相关）：**

**第二行：**

根据需要重复第二数据行，以定义要输出到输出数据库的变量列表。




