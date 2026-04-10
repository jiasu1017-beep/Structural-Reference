# *DEBOND





### *DEBOND激活裂纹扩展能力并指定脱粘振幅曲线。

此选项用于指定最初部分粘合的两个表面之间可能发生裂纹扩展。[*FRACTURE CRITERION](ch06abk33.md) 选项必须紧跟在此选项之后。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

##### **参考：**

- ["裂纹扩展分析，" Abaqus分析用户指南第11.4.3节](../usb/usb-link.md#usb-anl-acrackpropagation)
- [*FRACTURE CRITERION](ch06abk33.md)

### **必需参数：**

MASTER

将此参数设置为裂纹扩展分析中使用的接触对的主表面名称。

SLAVE

将此参数设置为裂纹扩展分析中使用的接触对的从表面名称。

### **可选参数：**

DEBONDING FORCE

如果裂纹尖端两个表面之间的牵引力要在脱粘后的下一个增量中立即释放，则设置 DEBONDING FORCE=STEP（默认）。

如果裂纹尖端两个表面之间的牵引力要在脱粘后逐渐在前面的增量中释放以避免突然的稳定性损失，则设置 DEBONDING FORCE=RAMP。

此参数仅在 [*FRACTURE CRITERION](ch06abk33.md) 选项上使用 TYPE=VCCT 或 TYPE=ENHANCED VCCT 时相关。

FREQUENCY

将此参数设置为输出频率（以增量计）。除非 FREQUENCY=0，否则裂纹尖端位置和相关量总是在每个步骤的最后一个增量中打印。默认值为 FREQUENCY=1。设置 FREQUENCY=0 以抑制此输出。

OUTPUT

如果省略此参数，裂纹扩展信息将打印在数据（`.dat`）文件中，但不会存储在结果（`.fil`）文件中。

设置 OUTPUT=FILE 以将裂纹扩展信息存储在结果文件中。

设置 OUTPUT=BOTH 以在数据文件中打印裂纹扩展信息并将其存储在结果文件中。

TIME INCREMENT

将此参数设置为自动时间增量的建议时间增量，用于脱粘开始后的第一个增量。默认值为下面数据行给出的最后一个相对时间。

对于固定时间增量，如果 Abaqus/Standard 发现其需要的时间增量小于当前值，则此参数的值将在脱粘开始后用作时间增量。时间增量大小将根据需要修改，直到脱粘完成。

### **定义脱粘振幅曲线的数据行：**

**第一行：**

根据需要重复此数据行以定义脱粘振幅曲线。




