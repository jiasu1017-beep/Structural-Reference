# *ELEMENT RESPONSE









### *ELEMENT RESPONSE定义设计灵敏度分析的单元响应。

此选项用于将计算在积分点的单元响应灵敏度写入输出数据库。它必须与[*DESIGN RESPONSE](ch04abk17.md)选项结合使用。

**产品：**Abaqus/Design

**类型：**历史数据

**级别：**步骤

##### **参考：**

- ["设计灵敏度分析，" Abaqus分析用户指南第19.1.1节](../usb/usb-link.md#usb-anl-adsa)
- [*DESIGN RESPONSE](ch04abk17.md)

### **可选参数：**

ELSET

将此参数设置为正在为其进行灵敏度输出的单元集名称。

### **请求单元灵敏度输出的数据行：**

**第一行：**

根据需要重复此数据行，以定义要将其灵敏度写入输出数据库的单元响应。




