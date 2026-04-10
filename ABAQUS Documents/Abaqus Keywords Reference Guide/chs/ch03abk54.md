# *CONTACT






### *CONTACT开始通用接触的定义。

此选项用于指示通用接触定义的开始。通用接触定义的各个方面通过将其他选项与 [*CONTACT](ch03abk54.md) 选项结合使用来指定。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据或历史数据  

**级别：**模型、步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["在 Abaqus/Standard 中定义通用接触相互作用，" Abaqus 分析用户指南第 36.2.1 节](../usb/usb-link.md#usb-cni-acontactgeneralstd)
- ["在 Abaqus/Explicit 中定义通用接触相互作用，" Abaqus 分析用户指南第 36.4.1 节](../usb/usb-link.md#usb-cni-acontactgeneral)

### **可选参数：**

OP

此参数仅适用于 Abaqus/Explicit。

设置 OP=MOD（默认）以相对于前一步骤修改现有的通用接触定义。

设置 OP=NEW 以删除任何先前指定的通用接触定义并指定新的定义。当通用接触定义被指定为模型数据时，OP=NEW 将被忽略。

### **此选项没有关联的数据行。**




