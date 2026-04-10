# *DESIGN RESPONSE





### *DESIGN RESPONSE指定设计灵敏度分析的响应。

此选项用于将接触、单元、节点和/或特征模式响应的灵敏度写入输出数据库。[*CONTACT RESPONSE](ch03abk72.md)、[*ELEMENT RESPONSE](ch05abk11.md) 和/或 [*NODE RESPONSE](ch14abk13.md) 选项可与此选项结合使用。

**产品：**Abaqus/Design  

**类型：**历史数据 

**级别：**步骤

##### **参考：**

- ["设计灵敏度分析，" Abaqus分析用户指南第19.1.1节](../usb/usb-link.md#usb-anl-adsa)
- [*CONTACT RESPONSE](ch03abk72.md)
- [*ELEMENT RESPONSE](ch05abk11.md)
- [*NODE RESPONSE](ch14abk13.md)

### **可选参数：**

FREQUENCY

将此参数设置为响应灵敏度的输出频率。输出将始终在最后一个增量时写入输出数据库。如果省略此参数，则将在分析的每个增量时写入输出。设置 FREQUENCY=0 以抑制响应灵敏度的输出。此参数还控制总DSA公式的灵敏度计算频率。

MODE LIST

包含此参数以表示将要列出其灵敏度的特征模式列表将在数据行上给出。此参数仅在 [*FREQUENCY](ch06abk35.md) 程序中有效。

### **如果包含 MODE LIST 参数，列出所需特征模式的数据行：**

**第一行：**

根据需要重复此数据行，以列出所有所需的特征模式。




