# *EL PRINT





### *EL PRINT定义单元变量的数据文件请求。

此选项用于提供单元变量（应力、应变等）的表格打印输出。

**产品：**Abaqus/Standard  

**类型：**历史数据 

**级别：**步骤

##### **参考：**

- ["输出到数据和结果文件，" Abaqus分析用户指南第4.1.2节](../usb/usb-link.md#usb-out-oprintfile)

### **可选参数：**

ELSET

将此参数设置为正在为其发出输出请求的单元集合名称。如果省略此参数，将为模型中的所有单元打印输出。

FREQUENCY

将此参数设置为输出频率（以增量计）。除非 FREQUENCY=0，否则输出将始终在每个步骤的最后增量打印。默认值为 FREQUENCY=1。设置 FREQUENCY=0 以抑制输出。

LAST MODE

此参数仅在自然频率特征值提取（["自然频率提取，" Abaqus分析用户指南第6.3.5节](../usb/usb-link.md#usb-anl-afreqextraction)）、复特征值提取（["复特征值提取，" Abaqus分析用户指南第6.3.6节](../usb/usb-link.md#usb-anl-acomplexfreqextract)）和特征值屈曲估计（["特征值屈曲预测，" Abaqus分析用户指南第6.2.3节](../usb/usb-link.md#usb-anl-aeigenbuckling)）期间有用。将此参数设置为需要输出的最高模式号。

默认值为 LAST MODE=*N*，其中 *N* 是提取的模式数。如果使用了 MODE 参数，则默认值为 LAST MODE=*M*，其中 *M* 是 MODE 参数的值。

MODE

此参数仅在自然频率提取、复特征值提取和特征值屈曲估计期间有用。将此参数设置为需要输出的第一模式号。默认值为 MODE=1。执行基于SIM的 [*FREQUENCY](ch06abk35.md) 分析（EIGENSOLVER=AMS、EIGENSOLVER=LANCZOS、SIM 或 EIGENSOLVER=SUBSPACE、SIM）时，特征向量始终按质量正则化。否则，正则化将遵循由 NORMALIZATION 参数设置的格式，默认为 DISPLACEMENT。

POSITION

如果正在打印的值是外推到集合中单元节点的值平均值，则设置 POSITION=AVERAGED AT NODES。由于具有不同属性的单元之间的变量可能不连续，Abaqus/Standard会将输出分成指定单元集合内不同单元属性定义的单独表格。Abaqus/Standard还将单独输出不同类型的单元。因此，平均仅在对节点有贡献的具有相同类型的单元上进行。

如果值被打印到单元质心（壳单元参考表面的质心，梁单元端节点之间的中点），则设置 POSITION=CENTROIDAL。

如果值被打印到实际计算变量的积分点，则设置 POSITION=INTEGRATION POINTS（默认）。

如果正在写入的值被外推到集合中每个单元的节点但不在节点处平均，则设置 POSITION=NODES。

REBAR

此参数可用于仅获取指定单元集合中钢筋的输出；将不给出基体材料的输出。它可以带值或不带值使用。如果不带值使用，则将为单元集合中的所有钢筋给出输出。可以将其设置为 [*REBAR](ch17abk11.md) 选项上分配给钢筋的名称，以指定该特定钢筋在单元集合中的输出。

如果在包含钢筋的模型中省略此参数，则输出请求控制仅基体材料的输出（截面力除外，其中钢筋中的力包含在力计算中）。

钢筋输出只能在连续体和梁单元的积分点获取。在壳和膜单元中，可以在积分点和单元质心处获取钢筋输出。

SUMMARY

设置 SUMMARY=YES（默认）以获取摘要以及表中每列最大值和最小值的位置。

设置 SUMMARY=NO 以抑制此摘要。

TOTALS

设置 TOTALS=YES 以打印表中每列的总和。例如，这对于求和一组合单元的能量很有用。默认值为 TOTALS=NO。

### **请求数据文件中单元输出的数据行：**

**第一行（可选，且仅在为其打印壳、梁或分层实体单元的积分点变量时相关）：**

**第二行：**

根据需要重复第二数据行：每行定义一个表格。如果省略此行，则不会将单元输出打印到数据文件。




