# *CONTACT INITIALIZATION DATA






### *CONTACT INITIALIZATION DATA为通用接触定义接触初始化方法。

此选项用于为 Abaqus/Standard 定义接触初始化方法。接触初始化方法使用 [*CONTACT INITIALIZATION ASSIGNMENT](ch03abk64.md) 选项应用于接触相互作用。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["在 Abaqus/Standard 中控制初始接触状态，" Abaqus 分析用户指南第 36.2.4 节](../usb/usb-link.md#usb-cni-agenlcontinitializationstd)
- ["与 Abaqus/Standard 中接触建模相关的常见困难，" Abaqus 分析用户指南第 39.1.2 节](../usb/usb-link.md#usb-cni-acontacttrouble)
- [*CONTACT](ch03abk54.md)
- [*CONTACT INITIALIZATION ASSIGNMENT](ch03abk64.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用此接触初始化方法。

### **可选的互斥参数：**

INITIAL CLEARANCE

将此参数设置为一个正值以指定初始间隙距离。

INTERFERENCE FIT

包含此参数但不设置其值，以将初始过盈作为干涉配合处理。

将此参数设置为一个正值以指定干涉距离。

如果省略此参数，则初始过盈将通过无应变调整来解决。

### **可选参数：**

MINIMUM DISTANCE

设置 MINIMUM DISTANCE=YES（默认）以在附近表面仅在单点接触时自动激活局部接触阻尼。

设置 MINIMUM DISTANCE=NO 以放弃此自动局部阻尼。

SEARCH ABOVE

将此参数设置为一个正值，以确保接触初始化的搜索区域包含至少与指定值一样大的间隙。

SEARCH BELOW

将此参数设置为一个正值，以确保接触初始化的搜索区域包含至少与指定值一样大的过盈。

### **此选项没有关联的数据行。**




