# *EL FILE





### *EL FILE定义单元变量的结果文件请求。

此选项用于选择在Abaqus/Standard分析中将写入结果（`.fil`）文件或在Abaqus/Explicit分析中将写入所选结果（`.sel`）文件的单元变量。在Abaqus/Explicit分析中，它必须与 [*FILE OUTPUT](ch06abk09.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE：**不支持；Abaqus/CAE 仅从输出数据库文件读取输出。

##### **参考：**

- ["输出到数据和结果文件，" Abaqus分析用户指南第4.1.2节](../usb/usb-link.md#usb-out-oprintfile)
- [*FILE OUTPUT](ch06abk09.md)

### **可选参数：**

DIRECTIONS

此参数仅适用于Abaqus/Standard分析。

此参数用于在请求分量输出时获取局部单元或材料坐标系的方向。对于使用局部坐标系的每个点，方向被写入为单独的记录。请参见["结果文件输出格式，" Abaqus分析用户指南第5.1.2节](../usb/usb-link.md#usb-out-fformat)，获取详细说明。

如果不应写入局部坐标方向，则设置 DIRECTIONS=NO（默认）。

如果应写入局部坐标方向，则设置 DIRECTIONS=YES。

ELSET

将此参数设置为正在为其发出输出请求的单元集合名称。如果省略此参数，将为模型中的所有单元写入输出。在Abaqus/Explicit分析中，也将为模型中的所有钢筋写入输出。在Abaqus/Standard分析中，必须包含 REBAR 参数以获取钢筋输出。

FREQUENCY

此参数仅适用于Abaqus/Standard分析。

将此参数设置为输出频率（以增量计）。除非 FREQUENCY=0，否则输出将始终在每个步骤的最后增量写入结果文件。默认值为 FREQUENCY=1。设置 FREQUENCY=0 以抑制输出。

LAST MODE

此参数仅适用于Abaqus/Standard分析。

此参数仅在自然频率的特征值提取（["自然频率提取，" Abaqus分析用户指南第6.3.5节](../usb/usb-link.md#usb-anl-afreqextraction)）和特征值屈曲估计（["特征值屈曲预测，" Abaqus分析用户指南第6.2.3节](../usb/usb-link.md#usb-anl-aeigenbuckling)）期间有用。将此参数设置为需要输出的最高模式号。

默认值为 LAST MODE=*N*，其中 *N* 是提取的模式数。如果使用了 MODE 参数，则默认值为 LAST MODE=*M*，其中 *M* 是 MODE 参数的值。

MODE

此参数仅适用于Abaqus/Standard分析。

此参数仅在自然频率的特征值提取（["自然频率提取，" Abaqus分析用户指南第6.3.5节](../usb/usb-link.md#usb-anl-afreqextraction)）和特征值屈曲估计（["特征值屈曲预测，" Abaqus分析用户指南第6.2.3节](../usb/usb-link.md#usb-anl-aeigenbuckling)）期间有用。将此参数设置为需要输出的第一模式号。默认值为 MODE=1。执行 [*FREQUENCY](ch06abk35.md) 分析时，正则化将遵循由 NORMALIZATION 参数设置的格式。否则，正则化使得模式中最大的位移分量大小为1.0。

POSITION

此参数仅适用于Abaqus/Standard分析。

如果正在写入的值是外推到集合中单元节点的值平均值，则设置 POSITION=AVERAGED AT NODES。由于具有不同属性的单元之间的变量可能不连续，Abaqus/Standard会将输出分成指定单元集合内不同单元属性定义的单独表格。Abaqus/Standard还将单独输出不同类型的单元。因此，平均仅发生在对具有相同类型的节点有贡献的单元上进行。

如果值被写入单元质心（壳单元参考表面的质心，梁单元端节点之间的中点），则设置 POSITION=CENTROIDAL。

如果值被写入实际计算变量的积分点，则设置 POSITION=INTEGRATION POINTS（默认）。

如果正在写入的值被外推到集合中每个单元的节点但不在节点处平均，则设置 POSITION=NODES。

REBAR

此参数仅适用于Abaqus/Standard分析。

此参数可用于仅获取指定单元集合中钢筋的输出；将不给出基体材料的输出。它可以带值或不带值使用。如果不带值使用，则将为单元集合中的所有钢筋给出输出。可以将其设置为 [*REBAR](ch17abk11.md) 选项上分配给钢筋的名称，以指定该特定钢筋在单元集合中的输出。

如果在包含钢筋的模型中省略此参数，则输出请求控制仅基体材料的输出（截面力除外，其中钢筋中的力包含在力计算中）。钢筋输出只能在连续体和梁单元的积分点获取。在壳和膜单元中，可以在积分点和单元质心处获取钢筋输出。

### **在Abaqus/Standard分析中请求结果文件中单元输出的数据行：**

**第一行（可选，且仅在为其打印壳、梁或分层实体单元的积分点变量时相关）：**

**第二行：**

根据需要重复第二数据行，以定义要输出到结果文件的变量列表。

### **在Abaqus/Explicit分析中请求所选结果文件中单元输出的数据行：**

**第一行：**

根据需要重复此数据行，以定义要输出到所选结果文件的变量列表。




