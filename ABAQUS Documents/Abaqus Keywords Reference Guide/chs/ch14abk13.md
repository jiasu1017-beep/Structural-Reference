# *NODE RESPONSE









### *NODE RESPONSE为设计灵敏度分析定义节点响应。

此选项用于将节点响应灵敏度写入输出数据库。它必须与[*DESIGN RESPONSE](ch04abk17.md)选项结合使用。

**产品：**Abaqus/Design  

**类型：**历史数据  

**级别：**步骤

##### **参考：**

- ["设计灵敏度分析，" Abaqus Analysis User's Guide第19.1.1节](../usb/usb-link.md#usb-anl-adsa)
- [*DESIGN RESPONSE](ch04abk17.md)

### **可选参数：**

NSET

将此参数设置为此灵敏度输出的节点集名称。

### **请求节点灵敏度输出的数据行：**

**第一行：**

根据需要重复此数据行以定义要写入输出数据库的节点响应灵敏度。