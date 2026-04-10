# *FILE FORMAT









### *FILE FORMAT指定结果文件输出格式并调用零增量结果文件输出。

此选项用于指定Abaqus/Standard结果文件输出的写入格式，并为分析中的所有有效过程调用零增量文件输出。此选项在分析中只能出现一次，且格式在重启动时无法更改。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型或历史数据

**级别：**模型，步骤

**Abaqus/CAE：**不支持；Abaqus/CAE不使用结果文件。

##### **参考：**

- ["输出，" Abaqus分析用户指南第4.1.1节](../usb/usb-link.md#usb-out-ooutput)

### **可选参数：**

ASCII

包含此参数以指定结果文件输出将以ASCII格式写入。如果省略[*FILE FORMAT](ch06abk08.md)选项或未使用此参数，则默认为写入二进制文件。

ZERO INCREMENT

包含此参数以指定应为分析中的所有有效过程在步骤开始时（零增量）写入结果文件输出。如果省略[*FILE FORMAT](ch06abk08.md)选项或未使用此参数，则默认情况下不会在零增量处写入输出。

**此选项没有关联的数据行。**



