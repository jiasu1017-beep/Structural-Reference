# *IMPORT






### *IMPORT从先前的 Abaqus/Explicit 或 Abaqus/Standard 分析导入信息。

此选项用于定义在先前的 Abaqus/Standard 或 Abaqus/Explicit 分析中导入指定节点和单元信息的时间。当从先前分析导入零件实例时，[*IMPORT](ch09abk04.md) 选项必须与 [*INSTANCE](ch09abk19.md) 选项一起使用。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 零件实例  

**Abaqus/CAE：** 支持与零件实例一起使用；使用 File 菜单支持导入存储在输出数据库中的选定零件实例；在 Load 模块中支持导入零件实例的初始状态。

##### **参考文献：**

- ["在 Abaqus 分析之间传输结果：概述，" Abaqus Analysis User's Guide 第 9.2.1 节](../usb/usb-link.md#usb-anl-atransferoverview)
- [*INSTANCE](ch09abk19.md)

### **必需参数：**

UPDATE

设置 UPDATE=NO 以继续分析而不重置参考配置。

设置 UPDATE=YES 以通过将参考配置重置为导入配置来继续分析。在这种情况下，位移和应变值从新参考配置计算。

### **可选的、互斥的参数：**

INCREMENT

当从 Abaqus/Standard 导入分析到 Abaqus/Explicit，或从一个 Abaqus/Standard 分析导入到另一个 Abaqus/Standard 分析时，将此参数设置为要从其导入分析的 Abaqus/Standard 重启文件上指定步骤的增量。如果省略此参数，则从指定步骤的最后一个可用增量导入分析。

INTERVAL

当从 Abaqus/Explicit 导入分析到 Abaqus/Standard，或从一个 Abaqus/Explicit 分析导入到另一个 Abaqus/Explicit 分析时，将此参数设置为要从其导入分析的 Abaqus/Explicit 状态文件上指定步骤的区间。如果省略此参数，则从指定步骤的最后一个可用区间导入分析。

ITERATION

此参数仅在从先前的直接循环 Abaqus/Standard 分析导入结果时相关。

当从 Abaqus/Standard 导入分析到 Abaqus/Explicit，或从一个 Abaqus/Standard 分析导入到另一个 Abaqus/Standard 分析时，将此参数设置为要从其导入分析的 Abaqus/Standard 重启文件上指定步骤的迭代号。由于在直接循环分析中，重启信息只能在迭代结束时写入，因此如果指定了 ITERATION 参数，则 INCREMENT 参数无关紧要并被忽略。如果省略此参数，则从指定步骤的最后一个可用迭代导入分析。

### **可选参数：**

STATE

设置 STATE=YES（默认）以导入指定步骤和指定区间、增量或迭代处单元的当前材料状态。

设置 STATE=NO 如果不导入材料状态。在这种情况下，单元将以无初始状态或以 [*INITIAL CONDITIONS](ch09abk18.md) 选项定义的状态开始。

STEP

将此参数设置为从中导入分析的 Abaqus/Explicit 状态文件或 Abaqus/Standard 重启文件上的步骤。如果省略此参数，则从指定增量、区间或迭代处的状态文件或重启文件的最后一个可用步骤导入分析。

### **指定要导入的单元集的数据行：**

**第一行：**

根据需要重复此数据行，以定义要导入的单元集。每个数据行最多可列出 16 个单元集。

### **导入零件实例没有数据行。**




